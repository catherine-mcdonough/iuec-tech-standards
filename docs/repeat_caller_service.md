# Repeat Caller Service

The Repeat Caller Service is a national service operated by HSCIC and is a core part of the Integrated Urgent Care national architecture.


## How does it work?

### Functions

The current functions provided by the Repeat Caller Service (RCS) is as follows:

- Respond to NHS 111 Repeat Caller Queries at the start of every NHS 111 encounter
- Receive NHS 111 CDA submissions at the end of every NHS 111 encounter


### Querying

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



### Submitting

Submitted documents are stored for a maximum of 96 hours before they are deleted.