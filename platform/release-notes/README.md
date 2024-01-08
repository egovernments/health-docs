# Release Notes

## Release Summary

The release offers new platform features and functions, the details of which are provided below.

### **Functional Changes**

* Added proximity-based search on household and individual.
*   Multi-round campaign enabled in the mobile app.

    \- Ability to configure cycles and deliveries.

    \- Formula to calculate the dosage based on criteria added in MDMS.
* Referral management and side-effects.
* Total count added in the household search.&#x20;
* Adding voucher tag (QR code) during beneficiary registration.
* Last-mile delivery with QR code (only BE - exchange of inventory between any users using user uuid scanned from logged in user profile code).
* Down sync API (v1.0).

### **Non-Functional Changes**

NA

## New ‌Feature Additions <a href="#new-feature-additions" id="new-feature-additions"></a>

| Feature             | Description                                                                                           |
| ------------------- | ----------------------------------------------------------------------------------------------------- |
| Side-effect         | Capture side-effects arising form medicine administration.                                            |
| Referral management | Refer said beneficiary to a health facility/worker in case of a side-effect.                          |
| Down sync API       | Download previous campaign registry from server for a new campaign or future cycles of same campaign. |

## Known Issues <a href="#known-issues" id="known-issues"></a>

* Down sync does not support incremental download (that is, downloading only new data created in the server since the last download).
