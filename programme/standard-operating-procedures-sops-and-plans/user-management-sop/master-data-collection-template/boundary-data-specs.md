# Boundary Data Specs

| Name of Field                        | Description                                                                                                                                              | Mandatory | Input | Data Type | Validation | Comments                                            | Need Data from Program/ State |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- | ----- | --------- | ---------- | --------------------------------------------------- | ----------------------------- |
| Sr. No.                              |                                                                                                                                                          |           |       |           |            |                                                     |                               |
| Boundary Code\*                      | This is a code for the sub-classification for a particular boundary. Should be unique across all boundaries defined                                      | Mandatory | MDMS  | String    |            |                                                     | Yes                           |
| Boundary Name\* (In English)         | The name of the boundary that is being defined in the English language                                                                                   | Mandatory | MDMS  | String    |            |                                                     | Yes                           |
| Boundary Name\* ( In Local Language) | The name of the boundary that is being defined in the local language of the state e.g. Portuguese, Hindi etc.                                            | Mandatory | MDMS  | String    |            |                                                     | Yes                           |
| Parent Boundary Code\*               | This is the boundary code of the parent which identifies to which parent the child belongs to                                                            | Mandatory | MDMS  | String    |            |                                                     | Yes                           |
| Boundary Type\*                      | The name of the boundary type i.e. Ward, Zone etc.                                                                                                       | Mandatory | MDMS  | String    |            |                                                     | Yes                           |
| Hierarchy Type Code\*                | The code of the [Boundary Hierarchies](https://digit-discuss.atlassian.net/wiki/spaces/DO/pages/424542339) for which this particular boundary is defined | Mandatory | MDMS  | String    |            |                                                     | Yes                           |
| Campaign Start Date                  | Date when campaign starts in the respective boundary in dd/mm/yyyy format                                                                                | Mandatory | MDMS  | Date      |            |                                                     | Yes                           |
| Campaign End Date                    | Date when campaign is supposed to end in the respective boundary in dd/mm/yyyy format                                                                    | Mandatory | MDMS  | Date      |            |                                                     | Yes                           |
| Total Households                     | Total households present in the boundary (as per microplan)                                                                                              | Mandatory | MDMS  | Numeric   |            |                                                     | Yes                           |
| Targetted Households                 | Total households targeted for the respective boundary (as per microplan)                                                                                 | Mandatory | MDMS  | Numeric   |            | For Bednet, total and targeted is likely to be same | Yes                           |
| Total Individuals                    | Total individuals present in the boundary (as per microplan)                                                                                             | Mandatory | MDMS  | Numeric   |            |                                                     | Yes                           |
| Targeted Individuals                 | Total individuals targeted in the boundary (as per microplan)                                                                                            | Mandatory | MDMS  | Numeric   |            | For Bednet, total and targeted is likely to be same | Yes                           |
| Bednets estimated to be delivered    | Total bednets estimated to be delivered in the boundary (as per microplan)                                                                               | Mandatory | MDMS  | Numeric   |            |                                                     | Yes                           |