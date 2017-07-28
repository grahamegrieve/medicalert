
To access a member's device list:

~~~~~~~~~~~~
GET [base]/DeviceUseStatement?patient=[id]
Content-Type: application/fhir+json
~~~~~~~~~~~~

The response will be a 200 OK containing a Bundle that contains zero or more 
DeviceUseStatement resources as described below.

Note that in this case, each of the DeviceUse resources will contain an 
additional <a href="StructureDefinition-Device.html">Device</a> resource with further details about the device. 


