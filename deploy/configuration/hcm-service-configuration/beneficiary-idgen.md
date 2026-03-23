# Beneficiary IDGen

## Overview

This document covers the configuration and operation of the Beneficiary ID Generation (IDGen) module. The service is designed to efficiently generate, allocate, and manage unique Beneficiary IDs, including support for high-throughput batch generation, dispatch to users/devices, validation, and status updates. The system uses both database and cache for optimal performance and is controlled via flexible configurations.

***

## Pre-requisites

* **PostgreSQL Database:**
  * All relevant tables for ID pool management must exist.
* **Redis Cache:**
  * Used for fast access to unassigned IDs and distributed locking (Redisson).
* **Kafka:**
  * For asynchronous status updates.
* **MDMS Setup:**
  * Role-based access and endpoint mappings must be configured.
* **Application Properties:**
  * Batch size, rate limits, ID format, and feature toggles should be set as per requirements.
* **API Gateway:**
  * Enforce API rate limiting.
* **User Roles:**
  * SYSTEM\_ADMINISTRATOR and DISTRIBUTOR roles must be defined in MDMS.

***

## Functionalities

### ID Generation

* **Batch Generation Endpoint:**
  * `POST /id_pool/_generate`
* **Function:**
  * Admin or system can trigger batch generation of unique beneficiary IDs, either manually or on a schedule.
* **Features:**
  * Batch size configurable (e.g., 1000 at a time).
  * Supports random (e.g., `[d{12}]`) and sequential (`[SEQ_ID_POOL_NUM]`) ID formats.
  * State prefix is configurable.
  * Ensures uniqueness with ON CONFLICT DO NOTHING in DB.

### ID Dispatching

* **Dispatch Endpoint:**
  * `POST /id_pool/_dispatch`
* **Function:**
  * DISTRIBUTORS can request a batch of unassigned IDs for a user/device.
* **Features:**
  * Acquires a distributed lock (Redisson) before assignment to ensure atomicity.
  * Uses Redis for quick allocation (fallback to DB if needed).
  * Enforces daily per-user cap (default: 100) and API rate limit (default: 4/sec).
  * Updates ID status to "ASSIGNED" and links to the user/device.
  * Emits Kafka event for every status update.

### ID Search and Status Update

* **Search Endpoint:**
  * `POST /id_pool/_search`
* **Update Endpoint:**
  * `POST /id_pool/_update`
* **Function:**
  * Allows searching IDs by various filters (ID, status, user, device, etc.).
  * Supports updating the status of IDs (e.g., mark as assigned, used, expired).

### ID Validation & Integration

* **Client Integration:**
  * Example: health-individual service validates the beneficiary ID during individual creation or update.
* **Validation Logic:**
  * Checks ID existence, uniqueness, and assignment status.
  * Accepts both the beneficiary ID and client reference ID.
  * Returns error for invalid, used, or missing IDs.
  * **Missing ID case:** All generated IDs are stored in the **ID Pool table**. If a client passes an ID of type **UNIQUE\_BENEFICIARY\_ID** that is not present in the pool, it is flagged as a missing ID.

***

## Deployment Details

* Deploy PostgreSQL and Redis with the required schemas and tables.
* Configure Kafka for asynchronous updates.
* Ensure API Gateway and MDMS are set up for rate limiting and endpoint/role mapping.
* Set environment/application properties for:
  * ID format
  * Batch size
  * Rate limits
  * Feature toggles (enable/disable generation & validation)
* Register all endpoints and their role mappings in MDMS.

***

## API Details

| Endpoint             | Method | Description                                          | Role                  |
| -------------------- | ------ | ---------------------------------------------------- | --------------------- |
| /id\_pool/\_generate | POST   | Batch generate unique beneficiary IDs                | SYSTEM\_ADMINISTRATOR |
| /id\_pool/\_dispatch | POST   | Dispatch unassigned IDs to user/device               | DISTRIBUTOR           |
| /id\_pool/\_search   | POST   | Search for IDs by filters                            | DISTRIBUTOR           |
| /id\_pool/\_update   | POST   | Update the status of an ID (assigned, used, expired) | DISTRIBUTOR           |

***

## Configuration Details

#### Data Model

* **Database: PostgreSQL**
  * Table `id_pool`: Stores all generated IDs and their status.
  * Unique constraint on `unique_beneficiary_id`.
* **Indexes:**
  * For fast lookup and uniqueness.
* **Cache: Redis**
  * Stores ready-to-dispatch IDs for quick allocation.
  * Used for distributed locking.

#### ID Format

* **Configured in:** `common-masters.IdFormat`
  * `id.pool.number.random`: `[d{12}]` (12-digit random)
  * `id.pool.number`: `[SEQ_ID_POOL_NUM]` (sequential)

#### Populator Type

* **Configured in:** `HCM.ID_TYPE_OPTIONS_POPULATOR`
  * Value: `UNIQUE_BENEFICIARY_ID`

#### Rate Limits

* **API Gateway:**
  * 4 requests/second (configurable)
* **User Rate Cap:**
  * 100 IDs/user/day (configurable)

#### Service Toggles

* **Enable/disable ID generation & validation**
* **Batch size**
* **Retry count**

### Role-Based Action Mapping (MDMS)

<table><thead><tr><th width="244.4375">Role</th><th>Action</th></tr></thead><tbody><tr><td>SYSTEM_ADMINISTRATOR</td><td>/id_pool/_generate</td></tr><tr><td>DISTRIBUTOR</td><td>/id_pool/_dispatch, /id_pool/_search, /id_pool/_update</td></tr></tbody></table>

* All API endpoints and their allowed roles must be registered in MDMS.

***

{% hint style="info" %}
### Notes

* The system ensures high reliability and concurrency using distributed locks and database constraints.
* All major configurations are managed via MDMS and application properties for flexibility.
* For future enhancements, additional ID types and assignment rules can be easily added.
{% endhint %}

***
