---
description: v1.8 - Attendance feature functional and technical release details
---

# Attendance Release Notes

## Functional Release Highlights

### What’s New?

* **QR Code Proof of Work for Attendance**
  * Every employee now gets a unique QR code.
  * Supervisors use the mobile app to scan the QR code and mark attendance.
  * This works even without internet; data syncs when a connection is available.
  * Both mobile and non-mobile employees are covered.
  * The overall attendance process doesn’t change, but now you must scan a QR code for proof.

#### Why is This Important?

* Stops “proxy” (fake) attendance and manual tampering.
* Makes attendance more trustworthy and easy to verify.
* Keeps things simple for supervisors.
* Prepares for future features like location and time stamping.

***

## Technical Release Highlights

### What’s New?

* **Tagging Employees for Better Grouping and Search**
  * You can now add a “tag” (like “SHIFT”, “PROJECT”, or “SKILL”) to each attendee.
  * Tags help you organise and filter attendance records easily.
* **Bulk Tag Update API**
  * New API: `POST /attendee/v1/_updateTag`
  * Lets you update tags for many attendees at once.
  * Validates input to make sure tags and attendees are correct.
* **Tag Search**
  * You can now search for attendees using tags in `/attendee/v1/_search`.
  * Supports searching with one or more tags.
* **Database Updates**
  * A new “tag” column was added to the attendance table for fast searching.
  * Database and config updated to handle tags in all attendance actions.
* **Code Improvements**
  * Added error messages for invalid tags and mismatches.
  * Cleaned up unused code.
  * Updated version to 1.3.0 to include these features.

***

## Summary Table

<table><thead><tr><th width="174.16015625">Feature</th><th>What It Does</th><th>Benefit</th></tr></thead><tbody><tr><td>QR Proof of Work</td><td>Scan QR to mark attendance</td><td>Stops fake/manual entries</td></tr><tr><td>Tagging</td><td>Add tags to group/filter attendees</td><td>Easier data analysis</td></tr><tr><td>Bulk Tag Update</td><td>Update tags for many attendees at once</td><td>Saves time</td></tr><tr><td>Tag-based Search</td><td>Search by one or more tags</td><td>Find the right records faster</td></tr><tr><td>Database/Code Clean</td><td>Support for tags, better error handling</td><td>More reliable and efficient</td></tr></tbody></table>

```
```
