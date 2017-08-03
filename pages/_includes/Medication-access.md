
To access a member's medications:

~~~~~~~~~~~~
GET [base]/MedicationStatement?patient=Patient/[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or more 
MedicationStatement resources as described below

Example: <http://test.healthintersections.com.au/medicalert/MedicationStatement?patient=Patient/1265489&_format=json>
