
To access a member's blood group details:

~~~~~~~~~~~~
GET [base]/Observation?patient=Patient/[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or one 
Observation resources as described below

Example: <http://test.healthintersections.com.au/medicalert/Observation?patient=Patient/1265489&_format=json>