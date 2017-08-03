
To access a member's doctor list:

~~~~~~~~~~~~
GET [base]/CareTeam?patient=Patient/[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or one 
CareTeam resources as described below. 

Example: <http://test.healthintersections.com.au/medicalert/CareTeam?patient=Patient/1265489&_format=json>

This CareTeam resource then references 1 or more <a href="StructureDefinition-Doctor.html">Doctor</a>
resources, which are then fetched by following the reference at CareTeam.participant.member. Rather than
fetching each of the Doctor resources independently, the server can return all the resources at once:

~~~~~~~~~~~~
GET [base]/CareTeam?patient=Patient/[id]&_include=CareTeam:participant
Content-Type: application/fhir+json
~~~~~~~~~~~~

This just saces repeated network calls with their associated latency.

Example: <http://test.healthintersections.com.au/medicalert/CareTeam?patient=Patient/1265489&_include=CareTeam:participant&_format=json>
