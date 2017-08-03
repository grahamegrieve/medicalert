
To access a member's Meical Warnings:

~~~~~~~~~~~~
GET [base]/Flag?patient=Patient/[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or more 
Flag resources as described below

Example: <http://test.healthintersections.com.au/medicalert/Flag?patient=Patient/1265489&_format=json>


