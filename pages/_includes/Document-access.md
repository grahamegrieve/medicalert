
To access a member's allergies:

~~~~~~~~~~~~
GET [base]/DocumentReference?patient=[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or more 
DocumentReference resources as described below

