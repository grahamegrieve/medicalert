
You don't access additional details about a Members device directly. 
Instead, to access the <a href="StructureDefinition-DeviceUse.html">Member's Device Use List</a>:

~~~~~~~~~~~~
GET [base]/DeviceUseStatement?patient=Patient/[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or more 
<a href="StructureDefinition-DeviceUse.html">DeviceUseStatement resources</a> 
as described below, each of which contains one of these resources described here.

Example: <http://test.healthintersections.com.au/medicalert/DeviceUseStatement?patient=Patient/1265489&_format=json>

