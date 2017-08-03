
To access a member's conditions:

~~~~~~~~~~~~
GET [base]/Condition?patient=Patient/[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or more 
Condition resources as described below

Example: <http://test.healthintersections.com.au/medicalert/Condition?patient=Patient/1265489&_format=json>