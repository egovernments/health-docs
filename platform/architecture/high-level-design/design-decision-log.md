# Design Decision Log

## Sync

1. Server should be responsible to handle or offer a mechanism to handle errors once data reaches it. (Error handling mechanism being designed by Platform).
2. Sync will be manually triggered by user (except for automatically syncing configuration down on first login).
3. Sync down of data is not required to supported (good to have) for first roll out.
4. Sync will be done through bulk APIs
5. Sync will send each save action performed by the field user while offline to the server to preserve an audit of actions performed by the field user.
   1. Eg: If a field user registers an individual and saves the record and then goes back to update the individual, this will result in 2 API calls to the server (one create and one update).
6. API Response compression Gzip will be turned on for all the endpoints
7. Unique identifier to be used between client and server
   1. Client will create a unique (client generated) identifier per entity (clientReferenceId) to relate entities while operations are being performed offline and send this id to the server for create operations.
   2. Any subsequent operations (like update, delete) will be on server gen id, so client has to get server gen id by searching using client generated id. Client will call search API with clientReferenceId and will get server generated id.&#x20;
   3. Client will update the server generated id into the records on the client and use the server generated id for subsequent updates for those entities
8. Processing on the backend will continue to be asynchronous and not changed for the health use case.

## Configurability

#### Backend

1. Search API max limit and default limit
2. Service details and endpoints

#### Frontend

1. Service details and endpoints
2. Number of entities sent to server in bulk API calls
3. Additional fields per entity in the app
4. The drop-down values or select options to be presented in the app for field users
5. Configuration changes are expected to be additive in order for the data captured against such configuration to continue being usable.
6. Number of retries on API call failure after which app should stop retrying
7. Timeout for API calls

## Access Control

1. Access to data will be defined by the linkages of staff to project and the corresponding boundary while respecting role-action mappings instead of the tenant based approach.

## Data

1. All deletes are soft deletes
2. Server is responsible to delete nested/child entities if applicable when the parent entity is deleted
3. Undeletion is not permitted
4. Duplicate updates do not need to be detected or filtered out. Client is responsible to send duplicate updates on entity as separate requests to server.
5. Since persistence in DIGIT is asynchronous but the sync process from the field worker app is likely to send dependent data in a short span of time, a cache is to be introduced against which dependent data can be validated if required while it is in the process of being persisted to the DB. This cache is exposed via the search API of the corresponding service and the caller is agnostic to whether the result was returned from cache or database.
6. For v1, we can maintain sequence of updates only for requests on a single entity by a single user. i.e. Updates on the same entity by multiple users will result in last caller's updates going through.
7. In order to maintain sequence of updates, a rowVersion field is introduced in every entity. Callers pass the rowVersion as received from the server. The server can detect if any out of sequence updates have come in and reject it / pass it to the error handling mechanism.
8. Search APIs will not return (soft) deleted data by default. If deleted data is required the includeDeleted param can be passed to the search APIs.

## Limitations

1. From the Product requirement perspective, there is no unique identification identifier,  so Platform is unable to check uniqueness of registry entities.
