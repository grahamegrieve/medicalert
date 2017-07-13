
To access a member's medications:

~~~~~~~~~~~~
GET [base]/MedicationStatement?patient=[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or more 
MedicationStatement resources as described below

