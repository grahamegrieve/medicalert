To fetch the member details, the client makes the following request:

~~~~~~~~
 GET [base]/Patient/[id]
 Content-Type: application/fhir+json
~~~~~~~~

where [id] is the Member number found on the bracelet/jewellery.

The operation will return 200 OK, with a patient resource (see below),
or a 404 Not Found error.

Example: <http://test.healthintersections.com.au/medicalert/Patient/1265489?_format=json>


