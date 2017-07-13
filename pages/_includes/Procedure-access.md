
To access a member's procedure history:

~~~~~~~~~~~~
GET [base]/Procedure?patient=[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or more 
Procedure resources as described below

