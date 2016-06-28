# Repeat Caller Service (RCS)

The Repeat Caller Service is a national service operated by HSCIC and is a core part of the Integrated Urgent Care national architecture.


## How does it work?

### Functionality

The current functions provided by the Repeat Caller Service (RCS) is as follows:

- Respond to NHS 111 Repeat Caller Queries at the start of every NHS 111 encounter
- Receive NHS 111 CDA submissions at the end of every NHS 111 encounter


### Querying The RCS

NHS 111 services are required to query the RCS at the beginning of each telephone encounter. The query contains a minimal set of patient demographics which are used to identify the caller.

Where a caller's identity has been verified against the Personal Demographics Service (PDS), their NHS number will be used as the primary identifier for the query.

Where a caller's identity has not been verified against PDS, the query will use additional demographic details to try and match the patient:

- First Name
- Last Name
- Date Of Birth
- Gender
- Postcode


Using the available search criteria, the RCS will respond to the query to answer the question "Has this caller already called twice in the last 96 hours?".

| If                                       | Then                                     |
| ---------------------------------------- | ---------------------------------------- |
| There are not two previous calls for the caller | The RCS will respond '**No**'            |
| There are two or more previous calls for the caller and the caller was identified by verified NHS number | The RCS will respond '**YES**' and will include the previous call reports in the response |
| There are two or more previous calls for the caller and the caller was identified using 4 or more of the 5 additional demographic details | The RCS will respond '**YES**' and will include the previous call reports in the response |
| There are two or more previous calls for the caller and the caller was identified using 3 of the 5 additional demographic details | The RCS will respond '**PARTIAL**' without including call reports, and the NHS 111 is prompted to ask the caller to confirm verbally |



### Submitting Documents To RCS

Submitted documents are stored for a maximum of 96 hours before they are deleted.

------



## Requirement for Integrated Systems

All IT systems used for receiving initial urgent care encounters must have connectivity to the Repeat Caller Service.

Systems should support both Repeat Caller Queries and CDA submissions at the end of encounters. 

### General

- All systems should submit a valid CDA document to the Repeat Caller Service upon completion of an encounter.

### Configurability

- The following settings should be configurable in the system without requiring new development / releases:
  - Ability to Enable / Disable Repeat Caller Service interactions
  - Endpoint URL for the Repeat Caller Service (endpoints for Submissions and Queries should be separately configured)
  - ​

### Submission Interface
#### Retry Logic
- If a submission attempt is unsuccessful, the submission should be queued to retry the submission.
- Systems should continue to retry the submission until a reasonable number of attempts have failed, or until submission is removed from the queue by a user.
- Systems should implement retry logic which increases the amount of time between retries with each subsequent retry. This is to ensure that retries attempts do not generate

#### Monitoring

- Systems should appropriate users to failure of submissions, and provide them with appropriate tools to monitor and respond to issues.

### Query Interface
