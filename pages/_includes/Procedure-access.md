
To access a member's procedure history:

~~~~~~~~~~~~
GET [base]/Procedure?patient=Patient/[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or more 
Procedure resources as described below

Example: <http://test.healthintersections.com.au/medicalert/Procedure?patient=Patient/1265489&_format=json>