
To access a member's doctor list:

~~~~~~~~~~~~
GET [base]/CareTeam?patient=[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or one 
CareTeam resources as described below. Note that this resource is different 
to all the others - the one care team resource lists all the dcotors associated
with the member, and each <a href="StructureDefinition-Doctor.html">Dcotor</a>
is contained within the CareTeam resource.

