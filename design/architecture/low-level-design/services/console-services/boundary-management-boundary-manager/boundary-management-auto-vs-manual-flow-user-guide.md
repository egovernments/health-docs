# Boundary Management - Auto vs Manual Flow (User Guide)

### What's the Difference?

```
  Think of it like naming files on your computer:
  - Auto Flow = Let the system name your files automatically (like "Document_1", "Document_2")
  - Manual Flow = You name your files yourself (like "Budget_Report", "Project_Plan")

  ---
  Auto Flow - Let the System Generate Codes

  When to Use Auto Flow?

  ✅ You're setting up boundaries for the first time✅ You don't have existing boundary codes✅ You want the system to handle code generation✅ You want a quick
  and easy setup

  How to Use Auto Flow?

  Step 1: Prepare Your Excel
  - Leave the "Boundary Code" column EMPTY
  - Fill in all other columns (Country, Province, District, etc.)

  Example Excel:
  | Country    | Province | District   | Boundary Code | ← Leave Empty!
  |------------|----------|------------|---------------|
  | Mozambique | Maputo   | KaMpfumo   |               | ← Empty
  | Mozambique | Maputo   | KaMubukwana|               | ← Empty
  | Mozambique | Gaza     | Xai-Xai    |               | ← Empty

  Step 2: Upload Your Excel
  - The system will automatically create codes like:
    - ADMIN_MO_C01 (for Mozambique)
    - ADMIN_MO_P01 (for Maputo)
    - ADMIN_MO_D01 (for KaMpfumo)

  Step 3: Done!
  - Download the processed file with generated codes

  ---
  Auto Flow - What Can Go Wrong?

  | ❌ Error          | 🔍 What It Means                 | ✅ How to Fix                                         |
  |------------------|----------------------------------|------------------------------------------------------|
  | Mixed Flow Error | Some rows have codes, some don't | Remove ALL codes or fill ALL codes                   |
  | Header Error     | Column names don't match         | Use exact names: ADMIN_COUNTRY, ADMIN_PROVINCE, etc. |
  | Flow Mismatch    | You used manual flow before      | Keep using manual flow or contact admin to reset     |
  | Missing Fields   | Empty cells in Country/Province  | Fill all hierarchy levels (no gaps)                  |

  ---
  Manual Flow - Provide Your Own Codes

  When to Use Manual Flow?

  ✅ You already have boundary codes from another system✅ You need specific naming conventions✅ You're integrating with existing data✅ You want full control
  over codes

  How to Use Manual Flow?

  Step 1: Prepare Your Excel
  - FILL the "Boundary Code" column with your codes
  - IMPORTANT: Every row must have a code (including parent boundaries!)

  Example Excel:
  | Country    | Province | District   | Boundary Code |
  |------------|----------|------------|---------------|
  | Mozambique |          |            | MZ_001        | ← Country code
  | Mozambique | Maputo   |            | MZ_MAP_001    | ← Province code
  | Mozambique | Maputo   | KaMpfumo   | MZ_MAP_KAM_01 | ← District code

  Step 2: Upload Your Excel
  - The system will use YOUR codes exactly as provided

  Step 3: Done!
  - Download the processed file with your codes

  ---
  Manual Flow - What Can Go Wrong?

  | ❌ Error             | 🔍 What It Means                       | ✅ How to Fix                           |
  |---------------------|----------------------------------------|----------------------------------------|
  | Missing Code        | A row doesn't have a code              | Fill boundary code for ALL rows        |
  | Missing Parent Code | District has code but Province doesn't | Add codes for ALL parent levels        |
  | Duplicate Code      | Same code appears twice                | Make sure each code is unique          |
  | Mixed Flow Error    | Some rows have codes, some don't       | Fill ALL rows with codes               |
  | Flow Mismatch       | You used auto flow before              | Keep using auto flow or contact admin  |
  | Code Already Exists | This code is already in the system     | Use a different code or remove the row |

  ---
  Quick Decision Guide

  ┌─────────────────────────────────────┐
  │ Do you have existing boundary codes?│
  └─────────────┬───────────────────────┘
                │
         ┌──────┴──────┐
         │             │
        YES            NO
         │             │
         ▼             ▼
     MANUAL FLOW   AUTO FLOW
     (Fill codes)  (Leave empty)

  ---
  Visual Comparison

  📊 Auto Flow Excel

  ✅ CORRECT:
  | Country    | Province | Boundary Code |
  |------------|----------|---------------|
  | Mozambique | Maputo   |               | ← Empty
  | Mozambique | Gaza     |               | ← Empty

  ❌ WRONG:
  | Country    | Province | Boundary Code |
  |------------|----------|---------------|
  | Mozambique | Maputo   | MAP_01        | ← Has code
  | Mozambique | Gaza     |               | ← Empty (Mixed!)

  📊 Manual Flow Excel

  ✅ CORRECT:
  | Country    | Province | Boundary Code |
  |------------|----------|---------------|
  | Mozambique |          | MZ_001        | ← Country code
  | Mozambique | Maputo   | MZ_MAP        | ← Province code
  | Mozambique | Gaza     | MZ_GAZ        | ← Province code

  ❌ WRONG:
  | Country    | Province | Boundary Code |
  |------------|----------|---------------|
  | Mozambique |          |               | ← Missing parent code!
  | Mozambique | Maputo   | MZ_MAP        | ← Has code

  ---
  Common Questions

  Q: Can I switch from Auto to Manual later?

  A: No, once you choose a flow, you must stick with it. Contact your system administrator if you need to change.

  Q: What if I make a mistake?

  A: The system will show you an error message. Read the error, fix your Excel, and upload again.

  Q: Can I use both flows in the same file?

  A: No! Choose one:
  - All codes empty = Auto Flow
  - All codes filled = Manual Flow

  Q: What happens if I upload the same data twice?

  A: The system is smart! It will:
  - Skip boundaries that already exist
  - Only create new boundaries
  - Update the file with all boundaries

  Q: Do I need to fill parent boundaries in Auto Flow?

  A: No! Just leave the code column empty. The system will generate codes for all levels automatically.

  Q: Do I need to fill parent boundaries in Manual Flow?

  A: Yes! Every boundary at every level must have a code.

  ---
  Step-by-Step Upload Process

  For Auto Flow Users:

  1. Download the boundary template
  2. Fill all columns EXCEPT "Boundary Code"
  3. Leave "Boundary Code" column empty
  4. Upload your Excel file
  5. Wait for processing (you'll see status: "accepted")
  6. Download the processed file with auto-generated codes

  For Manual Flow Users:

  1. Download the boundary template
  2. Fill all columns INCLUDING "Boundary Code"
  3. Make sure every row has a unique code
  4. Make sure all parent boundaries have codes
  5. Upload your Excel file
  6. Wait for processing (you'll see status: "accepted")
  7. Download the processed file with your codes

  ---
  Error Message Translation

  When you see an error, here's what it means in plain English:

  | Technical Error              | What It Really Means                                        |
  |------------------------------|-------------------------------------------------------------|
  | MIXED_BOUNDARY_FLOW          | You're mixing auto and manual - choose one!                 |
  | FLOW_MISMATCH_ERROR          | You changed the flow type - stick with what you used before |
  | MISSING_BOUNDARY_CODE        | (Manual only) You forgot to add a code in some row          |
  | MISSING_PARENT_BOUNDARY_CODE | (Manual only) Your district has a code but province doesn't |
  | DUPLICATE_BOUNDARY_CODE      | You used the same code twice - make them unique             |
  | BOUNDARY_SHEET_HEADER_ERROR  | Your column names are wrong - use the template              |
  | VALIDATION_ERROR             | Something's wrong with your data - check for empty cells    |

```
