# HCM Console Design

The platform architecture illustration below provides a visual representation of the key components and layers that facilitate a campaign creation flow in health campaign management.



<figure><img src="../../../.gitbook/assets/Screenshot 2025-09-22 at 11.23.26 AM.png" alt="HCM Console Architecture"><figcaption></figcaption></figure>





<figure><img src="../../../.gitbook/assets/UI Tech Designs - HLD (4).jpg" alt=""><figcaption><p>Console Web Flow</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/UI Tech Designs - HLD (2).jpg" alt=""><figcaption><p>Project Factory Flow</p></figcaption></figure>



Master Data&#x20;

The following are the various master data that will be used during the campaign creation process.

1. &#x20;Different types of campaign and delivery rules.
2. &#x20;Attributes on which delivery rules can be created.
3. &#x20;Schema to validate the Excel data for different templates.
4. &#x20;Parsing and transforming templates.
5. &#x20;Type to API mapping.
6. &#x20;App Configuration Templates & Actual Configs

More details on Master data can be accessed[ here](../../../deploy/configuration/hcm-console-configuration/)

#### Campaign Process&#x20;

<figure><img src="../../../.gitbook/assets/UI Tech Designs - 0.4.jpg" alt=""><figcaption><p>Campaign Process<br><br></p></figcaption></figure>

Click [here](../low-level-design/services/admin-console/) to know more.
