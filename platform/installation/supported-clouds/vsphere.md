# VSphere

## Overview

The Kubernetes vSphere driver contains bugs related to detaching volumes from offline nodes. See the [**Volume detach bug**](https://urban.digit.org/platform/installation/more-deploy-docs/infra-structure-overview/vsphere#volume-detach-bug) section for more details.

#### VM Images <a href="#vm-images" id="vm-images"></a>

When creating worker nodes for a user cluster, the user can specify an existing image. Defaults may be set in the [datacenters.yaml](https://docs.kubermatic.io/installation/install\_kubermatic/#defining-the-datacenters).Supported operating systems

* Ubuntu 18.04 [ova](https://cloud-images.ubuntu.com/releases/18.04/release/ubuntu-18.04-server-cloudimg-amd64.ova)​
* CoreOS [ova](https://stable.release.core-os.net/amd64-usr/current/coreos\_production\_vmware\_ova.ova)​
* CentOS 7 [qcow2](https://cloud.centos.org/centos/7/images/CentOS-7-x86\_64-GenericCloud.qcow2)​

#### **Importing the OVA** <a href="#importing-the-ova" id="importing-the-ova"></a>

1. 1.Go into the VSphere WebUI, select your data centre, right-click onto it and choose “Deploy OVF Template”
2. 2.Fill in the “URL” field with the appropriate URL
3. 3.Click through the dialogue until “Select storage”
4. 4.Select the same storage you want to use for your machines
5. 5.Select the same network you want to use for your machines
6. 6.Leave everything in the “Customize Template” and “Ready to complete” dialogue as it is
7. 7.Wait until the VM got fully imported and the “Snapshots” => “Create Snapshot” button is not greyed out anymore.
8. 8.The template VM must have the disk.enable UUID flag set to 1, this can be done using the [govc tool](https://github.com/vmware/govmomi/tree/master/govc) with the following command:

govc vm.change -e="disk.enableUUID=1" -vm='/PATH/TO/VM'

#### **Importing the QCOW2** <a href="#importing-the-qcow2" id="importing-the-qcow2"></a>

1. 1.Convert it to vmdk: `qemu-img convert -f qcow2 -O vmdk CentOS-7-x86_64-GenericCloud.qcow2 CentOS-7-x86_64-GenericCloud.vmdk`
2. 2.Upload it to a Datastore of your vSphere installation
3. 3.Create a new virtual machine that uses the uploaded vmdk as rootdisk.

#### **Modifications** <a href="#modifications" id="modifications"></a>

Modifications like Network, disk size, etc. must be done in the ova template before creating a worker node from it. If user clusters have dedicated networks, all user clusters, therefore, need a custom template.

#### VM Folder <a href="#vm-folder" id="vm-folder"></a>

During the creation of a user cluster Kubermatic creates a dedicated VM folder in the root path on the Datastore (Defined in the [datacenters.yaml](https://docs.kubermatic.io/installation/install\_kubermatic/#defining-the-datacenters)). That folder will contain all worker nodes of a user cluster.

#### Credentials / Cloud-Config <a href="#credentials-cloud-config" id="credentials-cloud-config"></a>

Kubernetes needs to talk to the vSphere to enable Storage inside the cluster. For this, kubernetes needs a config called `cloud-config`. This config contains all details to connect to a vCenter installation, including credentials.As this Config must also be deployed onto each worker node of a user cluster, its recommended to have individual credentials for each user cluster.

#### Permissions <a href="#permissions" id="permissions"></a>

The VSphere user must have the following permissions on the correct resources

#### **Seed Cluster** <a href="#seed-cluster" id="seed-cluster"></a>

* Role `k8c-storage-vmfolder-propagate`
  * Granted at **VM Folder** and **Template Folder**, propagated
  * Permissions
    * Virtual machine
      * Change Configuration
        * Add existing disk
        * Add new disk
        * Add or remove the device
        * Remove disk
    * Folder
      * Create folder
      * Delete folder
* Role `k8c-storage-datastore-propagate`
  * Granted at **Datastore**, propagated
  * Permissions
    * Datastore
      * Allocate space
      * Low-level file operations
* Role `Read-only` (predefined)
  * Granted at …, **not** propagated
    * Datacenter

#### **User Cluster** <a href="#user-cluster" id="user-cluster"></a>

* Role `k8c-user-vcenter`
  * Granted at **vcentre** level, **not** propagated
  * Needed to customize VM during provisioning
  * Permissions
    * VirtualMachine
      * Provisioning
        * Modify customization specification
        * Read customization specifications
* Role `k8c-user-datacenter`
  * Granted at **datacentre** level, **not** propagated
  * Needed for cloning the template VM (obviously this is not done in a folder at this time)
  * Permissions
    * Datastore
      * Allocate space
      * Browse datastore
      * Low-level file operations
      * Remove file
    * vApp
      * vApp application configuration
      * vApp instance configuration
    * Virtual Machine
      * Change CPU count
      * Memory
      * Settings
    * Inventory
      * Create from existing
* Role `k8c-user-cluster-propagate`
  * Granted at the **cluster** level, propagated
  * Needed for upload of `cloud-init.iso` (Ubuntu and CentOS) or defining the Ignition config into Guestinfo (CoreOS)
  * Permissions
    * Host
      * Configuration
        * System Management
      * Local operations
        * Reconfigure virtual machine
    * Resource
      * Assign virtual machine to the resource pool
      * Migrate powered off the virtual machine
      * Migrate powered-on virtual machine
    * vApp
      * vApp application configuration
      * vApp instance configuration
* Role k8s-network-attach
  * Granted for each network that should be used
  * Permissions
    * Network
      * Assign network
* Role `k8c-user-datastore-propagate`
  * Granted at **datastore/datastore cluster** level, propagated
  * Permissions
    * Datastore
      * Allocate space
      * Browse datastore
      * Low-level file operations
* Role `k8c-user-folder-propagate`
  * Granted at **VM Folder** and **Template Folder** level, propagated
  * Needed for managing the node VMs
  * Permissions
    * Folder
      * Create folder
      * Delete folder
    * Global
      * Set custom attribute
    * Virtual machine
      * Change Configuration
      * Edit Inventory
      * Guest operations
      * Interaction
      * Provisioning
      * Snapshot management

The described permissions have been tested with vSphere 6.7 and might be different for other vSphere versions.

#### **Volume Detach Bug** <a href="#volume-detach-bug" id="volume-detach-bug"></a>

After a node is powered-off, the Kubernetes vSphere driver doesn’t detach disks associated with PVCs mounted on that node. This makes it impossible to reschedule pods using these PVCs until the disks are manually detached in vCenter.Upstream Kubernetes has been working on the issue for a long time now and tracking it under the following tickets:

* ​[https://github.com/kubernetes/kubernetes/issues/63577](https://github.com/kubernetes/kubernetes/issues/63577)​
* ​[https://github.com/kubernetes/kubernetes/issues/61707](https://github.com/kubernetes/kubernetes/issues/61707)​
* ​[https://github.com/kubernetes/kubernetes/issues/67900](https://github.com/kubernetes/kubernetes/issues/67900)​
* ​[https://github.com/kubernetes/kubernetes/issues/71829](https://github.com/kubernetes/kubernetes/issues/71829)​
* ​[https://github.com/kubernetes/kubernetes/issues/75342](https://github.com/kubernetes/kubernetes/issues/75342)​

​[​![Creative Commons License](https://i.creativecommons.org/l/by/4.0/80x15.png)​](http://creativecommons.org/licenses/by/4.0/)All content on this page by [eGov Foundation](https://egov.org.in/) is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
