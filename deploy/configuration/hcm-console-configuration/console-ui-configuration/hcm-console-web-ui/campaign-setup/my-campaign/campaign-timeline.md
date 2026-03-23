# Campaign Timeline

## Overview

The timeline provides a visual representation of the campaign creation process. It can be accessed from the summary or through the action button on the "My Campaign" screen. The timeline will be shown for ongoing, upcoming, completed, and failed campaigns.

## Summary

<figure><img src="../../../../../../../.gitbook/assets/image (42).png" alt=""><figcaption><p>Timeline In summary page</p></figcaption></figure>

This timeline shows all the stages of the campaign that are successfully created. A user can download the user credentials as soon as the campaign is created successfully.

<figure><img src="../../../../../../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

&#x20;The above images show all three timeline steps: upcoming, current, and completed.

## My Campaign

A user can also access the timeline from the "My Campaign" screen by clicking on the action button present in the search result.

<figure><img src="../../../../../../../.gitbook/assets/image (44).png" alt=""><figcaption><p>Timeline in my campaign</p></figcaption></figure>

The timeline will be shown as a pop-up from the "My Campaign" screen. Similar to the summary, while the campaign creation is in progress, it will display all the steps such as upcoming, current, and completed. User credentials will be downloaded once the campaign is successfully created.

### File Path:

[https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/TimelineComponent.js](https://github.com/egovernments/DIGIT-Frontend/blob/campaign/micro-ui/web/micro-ui-internals/packages/modules/campaign-manager/src/components/TimelineComponent.js)

### API Details

| End point                                        | Method | Params                                              |
| ------------------------------------------------ | ------ | --------------------------------------------------- |
| /project-factory/v1/project-type/getProcessTrack | POST   | <p>params: { <br>campaignId: campaignId,<br> },</p> |
