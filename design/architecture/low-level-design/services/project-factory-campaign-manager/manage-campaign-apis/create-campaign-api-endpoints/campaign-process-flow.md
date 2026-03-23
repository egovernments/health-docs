# Campaign Process flow

#### **🔄 Simplified Parent-Child Campaign Management Design Flow** <a href="#wdpyk3g9un9q" id="wdpyk3g9un9q"></a>

**Core Principle**

At any point in time, only **one campaign**—either the **parent** or its successfully completed **child**—should be considered **active** and operational. A parent campaign remains active until a child campaign completes successfully and takes over its role.

#### **1️⃣ Initial Child Campaign Creation** <a href="#p8kg5i7y1qnl" id="p8kg5i7y1qnl"></a>

* **Validation:**<br>
  * Before creating a new child campaign, verify whether the parent already has a child campaign with:<br>
    * isActive: true<br>
  * If such a child exists, **reject the request** with an appropriate error.<br>
* **On Validation Pass:**<br>
  * Create the child campaign with:<br>
    * isActive: true (indicating it's currently being usable)<br>
    * status: 'draft' (or 'started'/'inprogress' based on next steps)<br>
    * parentId: set to the parent campaign's ID<br>
  * The **parent campaign** remains isActive: true.<br>
* **Why:** This ensures **only one active child** can exist at a time. The parent retains operational status while the child is in development.<br>

#### **2️⃣ During Child Campaign Processing (Update Phase)** <a href="#id-8gzz0qtetvh2" id="id-8gzz0qtetvh2"></a>

* The **child campaign** continues with:<br>
  * isActive: true<br>
  * status reflecting progress (e.g., inprogress, validating)<br>
* The **parent campaign** remains:<br>
  * isActive: true<br>
* **Why:** The child is actively being updated, but hasn't yet taken over. The parent remains the official operational campaign.<br>

#### **3️⃣ On Successful Child Campaign Completion** <a href="#c6aae8pgsk56" id="c6aae8pgsk56"></a>

* Once the child campaign is fully processed and marked status: 'completed':<br>
  * Child remains isActive: true<br>
  * Parent's isActive is updated to false<br>
* **Why:** This marks the official **handoff**. The child becomes the sole operational campaign, and the parent is retired from active use.<br>

#### **4️⃣ Cancelling a Child Campaign** <a href="#id-87p53uigygye" id="id-87p53uigygye"></a>

* If a child campaign is needed to be cancelled:<br>
  * Set its isActive: false
* **Why:** The child is clearly marked as non-operational. The parent continues as the active campaign, and a new child can be initiated later.<br>

#### **5️⃣ On Failed Child Campaign Creation/Update** <a href="#f8itgfzntof" id="f8itgfzntof"></a>

* If a failure occurs during child creation/update:<br>
  * Keep isActive: true<br>
  * Set status: 'failed'<br>
  * Parent remains isActive: true<br>
* **Why:** The failed child still exists and can be retried. The parent remains active. If it’s decided not to retry the child, it can later be **cancelled** (setting isActive: false).<br>

### **🔍 Campaign Search Functionality** <a href="#q599w1pi8uwp" id="q599w1pi8uwp"></a>

#### **Approach: Enhance the existing searchProjectTypeCampaignService and searchProjectCampaignResourcData.** <a href="#ubs605i986wi" id="ubs605i986wi"></a>

#### **Proposed Changes:** <a href="#dcynpptz2wx3" id="dcynpptz2wx3"></a>

**File: src/server/config/models/searchCampaignDetails.ts**

* Add:<br>
  * isChildCampaign?: boolean<br>
  * parentId?: string<br>

**File: src/server/utils/campaignUtils.ts → buildSearchQuery()**

* Modify query generation:<br>
  * If isChildCampaign === true, add AND parentId IS NOT NULL<br>
  * If isChildCampaign === false, add AND parentId IS NULL<br>
  * If parentId is specified, add AND parentId = $X<br>

#### **🔎 How to Search** <a href="#zer3n18jhn69" id="zer3n18jhn69"></a>

**1. All child campaigns:**

{

"tenantId": "yourTenantId",

"isChildCampaign": true

}

**2. Currently active (parent or completed child):**

{

"tenantId": "yourTenantId",

"isActive": true,

"status": "completed" // optional

}

**3. Cancelled or inactive child campaigns:**

{

"tenantId": "yourTenantId",

"isChildCampaign": true,

"isActive": false

}

**4. Parent campaigns not yet replaced:**

{

"tenantId": "yourTenantId",

"isChildCampaign": false,

"isActive": true

}

### **⚙️ Code-Level Integration**  <a href="#id-5pgtsryi9amo" id="id-5pgtsryi9amo"></a>

#### **✅ Max One Active Child Validation** <a href="#jjvmw3uw9cmg" id="jjvmw3uw9cmg"></a>

* In createProjectTypeCampaignService or processBasedOnAction:<br>
  * Query for existing active children (isActive: true) before proceeding.<br>

#### **✅ Deactivating Parent After Child Completion** <a href="#yulnfbt5k1u" id="yulnfbt5k1u"></a>

* On child status transition to completed:<br>
  * Fetch parent campaign<br>
  * Set isActive = false<br>
  * Persist the update ( via Kafka)<br>

#### **✅ Campaign Cancellation API** <a href="#ibn3w2vtr6wp" id="ibn3w2vtr6wp"></a>

**Endpoint:**\
POST /project-factory/v1/project-type/cancel-campaign

**Purpose:**\
Cancels a campaign by setting:

* isActive = false<br>
* status = "cancelled"\
  The update is sent via Kafka.<br>

#### **🔧 Request Body** <a href="#xvbjlqwcfaw" id="xvbjlqwcfaw"></a>

{% include "../../../../../../../.gitbook/includes/expandable-code-block.md" %}

#### **🟢 Success Response (200)** <a href="#l0jhd1n7j7eo" id="l0jhd1n7j7eo"></a>

Returns updated campaign with:

* isActive: false<br>
* status: "cancelled"<br>

#### **🔁 Idempotency** <a href="#ljjxi77mv36r" id="ljjxi77mv36r"></a>

Safe to call multiple times. Same result is returned.

#### **🧩 Internals** <a href="#dji3v1lfwq7o" id="dji3v1lfwq7o"></a>

* Validates inputs<br>
* Fetches campaign<br>
* Updates status<br>
* Produces to Kafka topic
