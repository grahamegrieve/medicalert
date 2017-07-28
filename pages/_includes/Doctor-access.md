
You don't access additional details about a Members device directly. 
Instead, to access the <a href="StructureDefinition-DoctorList.html">Member's Doctor List</a>:

~~~~~~~~~~~~
GET [base]/DeviceUseStatement?patient=[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or one
<a href="StructureDefinition-DoctorList.html">CareTeam resources</a>, 
which contains one or more of these resources described here.

