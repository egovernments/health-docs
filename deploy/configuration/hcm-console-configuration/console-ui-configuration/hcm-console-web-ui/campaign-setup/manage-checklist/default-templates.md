# Default Templates

The following is the procedure to configure default templates for checklists for different roles and types of checklists.

Following is the curl to create a template for:

The user needs to create a template for all the combinations of roles, campaign types, and checklist types for which he/she want to have a checklist configured.

```postman_json
"role": "DISTRIBUTOR",
"campaignType": "IRS-mz",
"checklistType": "TRAINING_SUPERVISION"
```

```
curl --location 'http://localhost:8081/mdms-v2/v2/_create/HCM-ADMIN-CONSOLE.ChecklistTemplates' \
--header 'accept: application/json, text/plain, */*' \
--header 'accept-language: en-GB,en-US;q=0.9,en;q=0.8' \
--header 'content-type: application/json;charset=UTF-8' \
--header 'cookie: _ga_H9YC8FEN6F=GS1.1.1703060128.1.1.1703060157.31.0.0; _ga_2E44ZSYXS7=GS1.1.1706788467.6.0.1706788467.0.0.0; _ga_0JZG96DZSM=GS1.1.1707896872.4.1.1707896889.43.0.0; amp_fef1e8=be028001-abe2-4879-ad17-f2999e099b9fR...1hmj9c8kb.1hmj9go83.27.g.2n; __cuid=7cd138a8619b4572a249bbec4504612f; _ga_XBQP06FR8V=GS1.1.1709707277.6.0.1709707277.60.0.0; _ga=GA1.1.1275395426.1703060110; _ga_P1TZCPKF6S=GS1.1.1711451018.1.1.1711451049.29.0.0' \
--header 'origin: https://unified-dev.digit.org' \
--header 'priority: u=1, i' \
--header 'referer: https://unified-dev.digit.org/workbench-ui/employee/workbench/mdms-add-v2?moduleName=HCM&masterName=BACKEND_INTERFACE' \
--header 'sec-ch-ua: "Chromium";v="124", "Google Chrome";v="124", "Not-A.Brand";v="99"' \
--header 'sec-ch-ua-mobile: ?0' \
--header 'sec-ch-ua-platform: "Linux"' \
--header 'sec-fetch-dest: empty' \
--header 'sec-fetch-mode: cors' \
--header 'sec-fetch-site: same-origin' \
--header 'user-agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/124.0.0.0 Safari/537.36' \
--data '{
    "Mdms": {
        "tenantId": "mz",
        "schemaCode": "HCM-ADMIN-CONSOLE.ChecklistTemplates",
        "uniqueIdentifier": null,
        "data": {
            "data": [
                {
                    "id": "2d4a7b1e-1f2f-4a8a-9672-43396c6c9a1c",
                    "key": 1,
                    "type": {
                        "code": "SingleValueList"
                    },
                    "level": 1,
                    "title": "Is there a feedback system for health facilities to report any issues or requests related to bednet distribution?",
                    "value": null,
                    "options": [
                        {
                            "id": "0cff9846-03a2-4453-bf0e-200cdda5f390",
                            "key": 1,
                            "label": "Shortages",
                            "optionComment": true,
                            "optionDependency": false,
                            "parentQuestionId": "2d4a7b1e-1f2f-4a8a-9672-43396c6c9a1c"
                        },
                        {
                            "id": "2d4a7b1e-7c0d-48b1-9d53-8601c6264b90",
                            "key": 2,
                            "label": "Quality complaints",
                            "optionDependency": false,
                            "parentQuestionId": "2d4a7b1e-1f2f-4a8a-9672-43396c6c9a1c"
                        }
                    ],
                    "isActive": true,
                    "parentId": null,
                    "isRequired": false
                },
                {
                    "id": "4add5323-fc98-4e71-a783-27dbb922c99f",
                    "key": 2,
                    "type": {
                        "code": "SingleValueList"
                    },
                    "level": 1,
                    "title": "What types of health facilities do you distribute to?",
                    "value": null,
                    "options": [
                        {
                            "id": "34eac43a-e0b5-428f-9d11-12fc5b10b1ac1",
                            "key": 1,
                            "label": "Hospitals",
                            "optionComment": false,
                            "optionDependency": false,
                            "parentQuestionId": "4add5323-fc98-4e71-a783-27dbb922c99f"
                        },
                        {
                            "id": "23ace43b-e0b5-428f-9d11-12fc5b10b1ac1",
                            "key": 2,
                            "label": "Clinics",
                            "optionComment": false,
                            "optionDependency": true,
                            "parentQuestionId": "4add5323-fc98-4e71-a783-27dbb922c99f"
                        },
                        {
                            "id": "32bbca43-db87-469b-8be4-22012cc22284",
                            "key": 3,
                            "label": "Community health centers",
                            "optionDependency": false,
                            "parentQuestionId": "4add5323-fc98-4e71-a783-27dbb922c99f"
                        }
                    ],
                    "isActive": true,
                    "parentId": null,
                    "isRequired": false
                },
                {
                    "id": "23ca54be-038e-42df-a557-bb5fcd374dd5",
                    "key": 3,
                    "type": {
                        "code": "SingleValueList"
                    },
                    "level": 1,
                    "title": "What services or products do you distribute to health facilities?",
                    "value": null,
                    "options": [
                        {
                            "id": "ea32bc56-038e-42df-a557-bb5fcd374dd5",
                            "key": 1,
                            "label": "Medical equipment",
                            "optionComment": false,
                            "optionDependency": false,
                            "parentQuestionId": "23ca54be-038e-42df-a557-bb5fcd374dd5"
                        },
                        {
                            "id": "a34vc429-d13f-4340-ae5e-fe7f8aca4212",
                            "key": 2,
                            "label": "Pharmaceuticals",
                            "optionDependency": false,
                            "parentQuestionId": "23ca54be-038e-42df-a557-bb5fcd374dd5"
                        },
                        {
                            "id": "6c43b57c-d13f-4340-ae5e-fe7f8aca4212",
                            "key": 3,
                            "label": "Personal protective equipment (PPE)",
                            "optionDependency": false,
                            "parentQuestionId": "23ca54be-038e-42df-a557-bb5fcd374dd5"
                        }
                    ],
                    "isActive": true,
                    "parentId": null,
                    "isRequired": false
                },
                {
                    "id": "c65ac34b-7cc0-4993-a8fe-37e854d2b189",
                    "key": 4,
                    "type": {
                        "code": "SingleValueList"
                    },
                    "level": 2,
                    "title": "Do you have enough products for distribution to health facilities?",
                    "value": null,
                    "options": [
                        {
                            "id": "cb45ca84-7cc0-4993-a8fe-37e854d2b189",
                            "key": 1,
                            "label": "Yes",
                            "optionDependency": false,
                            "parentQuestionId": "c65ac34b-7cc0-4993-a8fe-37e854d2b189"
                        },
                        {
                            "id": "a54c73cb-60da-4c51-8501-cf4a4f473a66",
                            "key": 2,
                            "label": "No",
                            "optionComment": true,
                            "optionDependency": false,
                            "parentQuestionId": "c65ac34b-7cc0-4993-a8fe-37e854d2b189"
                        }
                    ],
                    "isActive": true,
                    "parentId": "23ace43b-e0b5-428f-9d11-12fc5b10b1ac1",
                    "isRequired": false
                }
            ],
            "role": "DISTRIBUTOR",
            "campaignType": "IRS-mz",
            "checklistType": "TRAINING_SUPERVISION"
        },
        "isActive": true
    },
    "RequestInfo": {
        "apiId": "asset-services",
        "ver": null,
        "ts": null,
        "action": null,
        "did": null,
        "key": null,
        "msgId": "search with from and to values",
        "authToken": "",
        "correlationId": null,
        "userInfo": {
            "id": "1",
            "userName": null,
            "name": null,
            "type": null,
            "mobileNumber": null,
            "emailId": null,
            "roles": null,
            "uuid": "db842ca9-25c5-4419-a72f-459443d38feb"
        }
    }
}'
```

If any option needs to have sub-questions, then add an optionDependency attribute as true in the option's object. All the questions, whether at the parent or children level, need to be different objects and connected via their parentId which is nothing but the parent option's ID.

{% tabs %}
{% tab title="Single Value Correct" %}
```
{
    "id": "2d4a7b1e-1f2f-4a8a-9672-43396c6c9a1c",
    "key": 1,
    "type": {
        "code": "SingleValueList"
    },
    "level": 1,
    "title": "Is there a feedback system for health facilities to report any issues or requests related to bednet distribution?",
    "value": null,
    "options": [
        {
            "id": "0cff9846-03a2-4453-bf0e-200cdda5f390",
            "key": 1,
            "label": "Shortages",
            "optionComment": true,
            "optionDependency": false,
            "parentQuestionId": "2d4a7b1e-1f2f-4a8a-9672-43396c6c9a1c"
        },
        {
            "id": "2d4a7b1e-7c0d-48b1-9d53-8601c6264b90",
            "key": 2,
            "label": "Quality complaints",
            "optionDependency": false,
            "parentQuestionId": "2d4a7b1e-1f2f-4a8a-9672-43396c6c9a1c"
        }
    ],
    "isActive": true,
    "parentId": null,
    "isRequired": false
}
```

The question object is represented as a JSON structure with the following key properties:

1. **`id`** (String, Required)
   * A unique identifier for the question.
   * Example: `"2d4a7b1e-1f2f-4a8a-9672-43396c6c9a1c"`
2. **`key`** (Integer, Required)
   * The question's sequence or order in the questionnaire.
   * Example: `1`
3. **`type`** (Object, Required)
   * Represents the type of the question.
   * Contains a `code` field to specify the question type.
   * Example: `{ "code": "SingleValueList" }`
4. **`level`** (Integer, Required)
   * Indicates the hierarchy level of the question.
   * Example: `1` (Top-level question)
5. **`title`** (String, Required)
   * The text or content of the question.
   * Example: `"Is there a feedback system for health facilities to report any issues or requests related to bednet distribution?"`
6. **`value`** (String/Null, Optional)
   * Holds the selected value once a choice is made.
   * Initially `null`.
7. **`options`** (Array of Objects, Required)
   * A list of predefined choices for the question.
   * Each option includes:
     * **`id`**: Unique identifier for the option.
     * **`key`**: Sequence/order of the option.
     * **`label`**: Text describing the option.
     * **`optionComment`**: (Boolean) Indicates if a comment is allowed for the option.
     * **`optionDependency`**: (Boolean) Indicates if selecting the option triggers a dependent question.
     * **`parentQuestionId`**: Links the option to its parent question.
   *   Example:

       ```json
       {
           "id": "0cff9846-03a2-4453-bf0e-200cdda5f390",
           "key": 1,
           "label": "Shortages",
           "optionComment": true,
           "optionDependency": false,
           "parentQuestionId": "2d4a7b1e-1f2f-4a8a-9672-43396c6c9a1c"
       }
       ```
8. **`isActive`** (Boolean, Optional)
   * Indicates whether the question is active or visible in the form.
   * Example: `true`
9. **`parentId`** (String/Null, Optional)
   * Specifies the parent question ID if the question is a subquestion.
   * Example: `null` for top-level questions.
10. **`isRequired`** (Boolean, Optional)
    * Indicates if answering the question is mandatory.
    * Example: `false`
{% endtab %}

{% tab title="Multiple Value Corect" %}
```
{
    "id": "23ca54be-038e-42df-a557-bb5fcd374dd5",
    "key": 3,
    "type": {
        "code": "MultiValueList"
    },
    "level": 1,
    "title": "What services or products do you distribute to health facilities?",
    "value": null,
    "options": [
        {
            "id": "ea32bc56-038e-42df-a557-bb5fcd374dd5",
            "key": 1,
            "label": "Medical equipment",
            "optionComment": false,
            "optionDependency": false,
            "parentQuestionId": "23ca54be-038e-42df-a557-bb5fcd374dd5"
        },
        {
            "id": "a34vc429-d13f-4340-ae5e-fe7f8aca4212",
            "key": 2,
            "label": "Pharmaceuticals",
            "optionDependency": false,
            "parentQuestionId": "23ca54be-038e-42df-a557-bb5fcd374dd5"
        },
        {
            "id": "6c43b57c-d13f-4340-ae5e-fe7f8aca4212",
            "key": 3,
            "label": "Personal protective equipment (PPE)",
            "optionDependency": false,
            "parentQuestionId": "23ca54be-038e-42df-a557-bb5fcd374dd5"
        }
    ],
    "isActive": true,
    "parentId": null,
    "isRequired": false
}
```

The question object is represented as a JSON structure with the following key properties:

1. **`id`** (String, Required)
   * A unique identifier for the question.
   * Example: `"23ca54be-038e-42df-a557-bb5fcd374dd5"`
2. **`key`** (Integer, Required)
   * The question's sequence or order in the questionnaire.
   * Example: `3`
3. **`type`** (Object, Required)
   * Represents the type of the question.
   * Contains a `code` field to specify the question type.
   * Example: `{ "code": "MultiValueList" }`
4. **`level`** (Integer, Required)
   * Indicates the hierarchy level of the question.
   * Example: `1` (Top-level question)
5. **`title`** (String, Required)
   * The text or content of the question.
   * Example: `"What services or products do you distribute to health facilities?"`
6. **`value`** (Array/Null, Optional)
   * Holds the selected values once options are chosen.
   * Initially `null`.
7. **`options`** (Array of Objects, Required)
   * A list of predefined choices for the question.
   * Each option includes:
     * **`id`**: Unique identifier for the option.
     * **`key`**: Sequence/order of the option.
     * **`label`**: Text describing the option.
     * **`optionComment`**: (Boolean) Indicates if a comment is allowed for the option.
     * **`optionDependency`**: (Boolean) Indicates if selecting the option triggers a dependent question.
     * **`parentQuestionId`**: Links the option to its parent question.
   *   Example:

       ```json
       {
           "id": "ea32bc56-038e-42df-a557-bb5fcd374dd5",
           "key": 1,
           "label": "Medical equipment",
           "optionComment": false,
           "optionDependency": false,
           "parentQuestionId": "23ca54be-038e-42df-a557-bb5fcd374dd5"
       }
       ```
8. **`isActive`** (Boolean, Optional)
   * Indicates whether the question is active or visible in the form.
   * Example: `true`
9. **`parentId`** (String/Null, Optional)
   * Specifies the parent question ID if the question is a subquestion.
   * Example: `null` for top-level questions.
10. **`isRequired`** (Boolean, Optional)
    * Indicates if answering the question is mandatory.
    * Example: `false`
{% endtab %}

{% tab title="Nested Question" %}
```
{
    "id": "4add5323-fc98-4e71-a783-27dbb922c99f",
    "key": 2,
    "type": {
        "code": "SingleValueList"
    },
    "level": 1,
    "title": "What types of health facilities do you distribute to?",
    "value": null,
    "options": [
        {
            "id": "34eac43a-e0b5-428f-9d11-12fc5b10b1ac1",
            "key": 1,
            "label": "Hospitals",
            "optionComment": false,
            "optionDependency": false,
            "parentQuestionId": "4add5323-fc98-4e71-a783-27dbb922c99f"
        },
        {
            "id": "23ace43b-e0b5-428f-9d11-12fc5b10b1ac1",
            "key": 2,
            "label": "Clinics",
            "optionComment": false,
            "optionDependency": true,
            "parentQuestionId": "4add5323-fc98-4e71-a783-27dbb922c99f"
        },
        {
            "id": "32bbca43-db87-469b-8be4-22012cc22284",
            "key": 3,
            "label": "Community health centers",
            "optionDependency": false,
            "parentQuestionId": "4add5323-fc98-4e71-a783-27dbb922c99f"
        }
    ],
    "isActive": true,
    "parentId": null,
    "isRequired": false
},

{
    "id": "c65ac34b-7cc0-4993-a8fe-37e854d2b189",
    "key": 4,
    "type": {
        "code": "SingleValueList"
    },
    "level": 2,
    "title": "Do you have enough products for distribution to health facilities?",
    "value": null,
    "options": [
        {
            "id": "cb45ca84-7cc0-4993-a8fe-37e854d2b189",
            "key": 1,
            "label": "Yes",
            "optionDependency": false,
            "parentQuestionId": "c65ac34b-7cc0-4993-a8fe-37e854d2b189"
        },
        {
            "id": "a54c73cb-60da-4c51-8501-cf4a4f473a66",
            "key": 2,
            "label": "No",
            "optionComment": true,
            "optionDependency": false,
            "parentQuestionId": "c65ac34b-7cc0-4993-a8fe-37e854d2b189"
        }
    ],
    "isActive": true,
    "parentId": "23ace43b-e0b5-428f-9d11-12fc5b10b1ac1",
    "isRequired": false
}
```

The parent question object (`SingleValueList`) has the following properties:

1. **`id`** (String, Required)
   * A unique identifier for the question.
   * Example: `"4add5323-fc98-4e71-a783-27dbb922c99f"`
2. **`key`** (Integer, Required)
   * The order or sequence of the question.
   * Example: `2`
3. **`type`** (Object, Required)
   * Indicates the question type.
   * Example: `{ "code": "SingleValueList" }`
4. **`level`** (Integer, Required)
   * Denotes the hierarchy level. For parent questions, this is `1`.
   * Example: `1`
5. **`title`** (String, Required)
   * The content of the question.
   * Example: `"What types of health facilities do you distribute to?"`
6. **`value`** (String/Null, Optional)
   * Holds the selected value after a user chooses an option.
   * Initially `null`.
7. **`options`** (Array of Objects, Required)
   * A list of predefined choices, where:
     * **`optionDependency`**: Determines if selecting the option triggers a nested question.
   *   Example:

       ```json
       {
           "id": "23ace43b-e0b5-428f-9d11-12fc5b10b1ac1",
           "key": 2,
           "label": "Clinics",
           "optionDependency": true
       }
       ```
8. **`isActive`** (Boolean, Optional)
   * Specifies whether the question is active.
   * Example: `true`
9. **`parentId`** (String/Null, Optional)
   * `null` for top-level (parent) questions.
10. **`isRequired`** (Boolean, Optional)
    * Indicates if the question is mandatory.
    * Example: `false`

***

**Structure of Nested Question**

The nested question object is similar to the parent question but includes additional context linking it to the triggering parent question.

1. **`id`** (String, Required)
   * Unique identifier for the nested question.
   * Example: `"c65ac34b-7cc0-4993-a8fe-37e854d2b189"`
2. **`key`** (Integer, Required)
   * Sequence/order of the question.
   * Example: `4`
3. **`type`** (Object, Required)
   * Specifies the type of question.
   * Example: `{ "code": "SingleValueList" }`
4. **`level`** (Integer, Required)
   * The hierarchy level. Nested questions have a higher level (e.g., `2`).
   * Example: `2`
5. **`title`** (String, Required)
   * The text of the nested question.
   * Example: `"Do you have enough products for distribution to health facilities?"`
6. **`value`** (String/Null, Optional)
   * Holds the selected value after a user chooses an option.
   * Initially `null`.
7. **`options`** (Array of Objects, Required)
   * The predefined choices for the nested question.
   *   Example:

       ```json
       {
           "id": "a54c73cb-60da-4c51-8501-cf4a4f473a66",
           "key": 2,
           "label": "No",
           "optionComment": true
       }
       ```
8. **`isActive`** (Boolean, Optional)
   * Indicates whether the question is active.
   * Example: `true`
9. **`parentId`** (String, Required)
   * Links the nested question to the triggering parent option.
   * Example: `"23ace43b-e0b5-428f-9d11-12fc5b10b1ac1"`
10. **`isRequired`** (Boolean, Optional)
    * Specifies if the nested question is mandatory.
    * Example: `false`
{% endtab %}
{% endtabs %}
