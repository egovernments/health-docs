# End-to-End Process Flow

The system supports an Excel-based workflow for various health campaign types (e.g., boundary, user, facility). It provides a dynamic, config-driven approach for **template generation**, **data validation**, and **data processing**.

### **🔁 Overall Flow:** <a href="#id-6xnonvkspiw7" id="id-6xnonvkspiw7"></a>

**Generate Template → Fill Data → Upload & Validate → Process Data**

### **1. 📄 Template Generation Flow (generateFlowClasses)** <a href="#nd42t0tv0mha" id="nd42t0tv0mha"></a>

The template generation process creates structured Excel templates with localized headers, metadata, and placeholder content based on the campaign type.

#### **A. Configuration – generationTemplateConfigs.ts** <a href="#hltjjt9xc0qy" id="hltjjt9xc0qy"></a>

Defines the sheet structure and metadata for each campaign type:

```json
boundary: {
sheets: [
{
sheetName: "HCM_README_SHEETNAME",
schemaName: "target-readme",
lockWholeSheet: true
}
]
}
```

#### **B. Generate Classes – e.g., boundary-generateClass.ts** <a href="#t1fowgkn4kys" id="t1fowgkn4kys"></a>

**Purpose**: Dynamically generate campaign-specific Excel templates.

**Key Method**: TemplateClass.generate()

**Steps:**

1. Fetch campaign details from DB<br>
2. Load boundary hierarchy and relationships<br>
3. Localize boundary data and headers<br>
4. Generate readme and metadata sheets<br>
5. Create SheetMap with structured data<br>
6. Return data to generate Excel<br>

#### **C. Template Generation Process – sheetManageUtils.ts** <a href="#gkx281figd7e" id="gkx281figd7e"></a>

```

export async function generateResource(responseToSend: any, templateConfig: any) {
// 1. Get localization maps
// 2. Load generate class dynamically
// 3. Generate SheetMap using TemplateClass.generate()
// 4. Create Excel file with localized structure
// 5. Upload to file store
// 6. Send status/event to Kafka
}
```

### **2. 🧩 Data Processing Flow (processFlowClasses)** <a href="#kv519y9753tg" id="kv519y9753tg"></a>

Handles the uploaded Excel file, validates it, and processes the data to create or update entities in the system.

#### **A. Configuration – processTemplateConfigs.ts** <a href="#id-647fswn1p25n" id="id-647fswn1p25n"></a>

Defines how to process uploaded Excel files:

```
boundary: {
sheets: [
{
sheetName: "HCM_README_SHEETNAME",
lockWholeSheet: true
}
],
enrichmentFunction: "enrichTargetProcessConfig"
}
```

#### **B. Process Classes – e.g., boundary-processClass.ts** <a href="#id-1idu89ueoguf" id="id-1idu89ueoguf"></a>

**Purpose**: Validate and persist uploaded data.

**Key Method**: TemplateClass.process()

**Steps:**

1. Validate resource details (file, campaign)<br>
2. Extract data from uploaded sheets<br>
3. Enrich data using boundary hierarchy<br>
4. Create/update boundary records<br>
5. Generate mapping and project data<br>
6. Process in topological (dependency-resolved) order<br>

#### **C. Validation Classes – e.g., boundaryValidation-processClass.ts** <a href="#id-9yde2kumv1ub" id="id-9yde2kumv1ub"></a>

**Purpose**: Perform schema-based and business-rule validations.

**Key Method**: TemplateClass.process()

**Steps:**

1. Validate against schema (column names, types)<br>
2. Check required vs optional columns<br>
3. Validate logical integrity (parent-child)<br>
4. Mark errors in Excel (cell comments, color)<br>
5. Return annotated Excel for user corrections<br>

#### **D. Data Processing Utility – sheetManageUtils.ts** <a href="#cinhiylz66ad" id="cinhiylz66ad"></a>

```
export async function processResource(ResourceDetails: any, templateConfig: any) {
// 1. Download Excel file from file store
// 2. Extract locale and sheet structure
// 3. Load localization maps
// 4. Dynamically load process/validation class
// 5. Perform validation and/or processing
// 6. Annotate sheet with validation results
// 7. Upload processed file
// 8. Send status/event to Kafka
}
```

### **3. 🔄 Complete End-to-End Flow** <a href="#id-8h3p9fe0kw2" id="id-8h3p9fe0kw2"></a>

#### **✅ Step 1: Template Generation** <a href="#zb02w94nqyde" id="zb02w94nqyde"></a>

* **Trigger**: User requests a template for a specific campaign type (e.g., boundary, user, facility)<br>
* **Process**:<br>
  1. Load configuration from generationTemplateConfigs<br>
  2. Fetch campaign data and related hierarchy<br>
  3. Dynamically import \*-generateClass.ts<br>
  4. Call TemplateClass.generate() to generate data<br>
  5. Generate Excel file with formatting, validation, and localization<br>
  6. Upload to file store<br>
* **Response**: Returns fileStoreId and generation status<br>

#### **✅ Step 2: Data Upload & Processing** <a href="#s3gmgj84ia" id="s3gmgj84ia"></a>

* **Upload**: User uploads the filled Excel template<br>

**🔍 Validation Phase (Optional)**

* Load validation class (e.g., boundaryValidation-processClass)<br>
* Validate against schema and business rules<br>
* Annotate errors directly in Excel file<br>
* Return Excel for correction<br>

**⚙️ Processing Phase**

* Load processing config and class (e.g., boundary-processClass)<br>
* Call TemplateClass.process() to:<br>
  * Extract and validate data<br>
  * Enrich using hierarchy<br>
  * Persist via Kafka (batch insert/update)<br>
* **Response**: Returns processed Excel and summary<br>

### **4. 🧠 Key Features** <a href="#bn1rvluoyi4" id="bn1rvluoyi4"></a>

#### **🔧 Dynamic Class Loading** <a href="#tp31ip6b5sgj" id="tp31ip6b5sgj"></a>

const className = \`${type}-generateClass\`; // or \`${type}-processClass\`

const classFilePath = path.join(\_\_dirname, '..', 'generateFlowClasses', \`${className}.ts\`);

const { TemplateClass } = await import(classFilePath);

* Plug-and-play support for new types (boundary, user, etc.)<br>
* Reduces code duplication<br>

#### **🌐 Localization Support** <a href="#pv9t1h5pibwz" id="pv9t1h5pibwz"></a>

* Detects locale from Excel metadata<br>
* Supports multilingual sheet names and headers<br>
* Error messages and field names localized dynamically<br>

#### **⚡ Kafka Integration** <a href="#uz7w7c3euo61" id="uz7w7c3euo61"></a>

* Asynchronous, scalable data ingestion<br>
* Sends status, logs, and errors to Kafka<br>
* Enables reliable batch processing<br>

#### **✅ Validation Framework** <a href="#lpa22zspru73" id="lpa22zspru73"></a>

* Schema-driven validation<br>
* Business rule enforcement<br>
* Marks errors with cell comments and styles<br>
* Supports required vs optional fields<br>

#### **🏗️ Hierarchical Data Processing** <a href="#f0qsvo6szq8n" id="f0qsvo6szq8n"></a>

* Handles parent-child boundary relationships<br>
* Uses topological sorting to maintain dependency order<br>
* Supports complex graph-based boundary structures<br>

### **5. 📦 Supported Sheet types** <a href="#bu7ges45y4sl" id="bu7ges45y4sl"></a>

| **Type**       | **Description**                   |
| -------------- | --------------------------------- |
| boundary       | Geographic boundary and hierarchy |
| user           | User onboarding and management    |
| facility       | Healthcare facility setup         |
| userCredential | Authentication data for users     |

Each type has:

* A **generate class** for template creation<br>
* A **process class** for data ingestion<br>
* A **validation class** for pre-checking data<br>
