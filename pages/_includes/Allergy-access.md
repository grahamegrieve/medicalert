
To access a member's allergies:

~~~~~~~~~~~~
GET [base]/AllergyIntolerance?patient=[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or more 
AllergyIntolerance resources as described below
