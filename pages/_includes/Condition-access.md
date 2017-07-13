
To access a member's conditions:

~~~~~~~~~~~~
GET [base]/Condition?patient=[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or more 
Condition resources as described below

