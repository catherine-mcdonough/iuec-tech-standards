# Repeat Caller Service

[TOC]

## What is the Repeat Caller Service?

The Repeat Caller Service is a national service operated by HSCIC and is a core part of the Integrated Urgent Care national architecture.

The current functions provided by the Repeat Caller Service (RCS) is as follows:

- Respond to NHS 111 Repeat Caller Queries at the start of every NHS 111 encounter
- Receive NHS 111 CDA submissions at the end of every NHS 111 encounter



## How does it work?

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

| If                                       | Then                                     | Status                  |
| ---------------------------------------- | ---------------------------------------- | ----------------------- |
| There are not two previous calls for the caller | The RCS will respond '**No**'            | Not A Repeat Caller     |
| There are two or more previous calls for the caller and the caller was identified by verified NHS number | The RCS will respond '**YES**' and will include the previous call reports in the response | Confirmed Repeat Caller |
| There are two or more previous calls for the caller and the caller was identified using 4 or more of the 5 additional demographic details | The RCS will respond '**YES**' and will include the previous call reports in the response | Confirmed Repeat Caller |
| There are two or more previous calls for the caller and the caller was identified using 3 of the 5 additional demographic details | The RCS will respond '**PARTIAL**' without including call reports, and the NHS 111 is prompted to ask the caller to confirm verbally | Potential Repeat Caller |



### Submitting Documents
Submitted documents are stored for a maximum of 96 hours before they are deleted.



## Implementation Requirements

All IT systems used for receiving initial urgent care encounters must have connectivity to the Repeat Caller Service.

Systems should support both Repeat Caller Queries and CDA submissions at the end of encounters. 



### Querying The Repeat Caller Service

Any system, that is used to manage people who are making first contact with Integrated Urgent Care, should query the Repeat Caller Service to identify whether that person has previously made contact with the Integrated Urgent Care service.

If a person is identified as having called twice previously within the preceeding 96 hours the service then they should be transferred to a clinician as a minimum level of priority (anything of a higher priority should be followed).





#### Submission

**All systems should submit a CDA document to the Repeat Caller Service upon completion of an encounter.**

#### Managing Failure
**If a submission attempt is unsuccessful, the system must continue trying to submit the document for 96 hours.**

**Systems should continue to retry the submission unless the queued submission is explcitly removed from the submission queue by a user.**



#### Configuration

**Systems should provide the ability to disable Repeat Caller Service queries when necessary.**

In the event that Repeat Caller Service queries are disabled, the system should always prompt the user to confirm whether the caller has called before to establish whether they are a repeat caller.