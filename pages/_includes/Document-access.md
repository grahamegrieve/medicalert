
To access a member's allergies:

~~~~~~~~~~~~
GET [base]/DocumentReference?patient=Patient/[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or more 
DocumentReference resources as described below

Example: <http://test.healthintersections.com.au/medicalert/DocumentReference?patient=Patient/1265489&_format=json>

