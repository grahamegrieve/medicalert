## {{ site.data.fhir.igName }} Implementation Guide
{:.no_toc}

{% include publish-box.html %}

This implementation guide describes how to use the shared Australia/New Zealand Medic Alert Web interface to gain access 
to a Medic Alert Member's Emergency Information. 

The Medic Alert interface is based on FHIR, an international specification for exchanging
healthcare data. For additional details, see <http://hl7.org/fhir>

# Process 

The overall process supported by the Medic Alert web service is very simple:

* an emergency worker is called to respond to a patient wearing a medic alert bracelet (etc)
* they enter the id number written on the bracelet into their medic alert access app (henceforth known is 'the client')
* the client requests for information from the appropriate medic alert server ('the server')
* the server responds with the set of information that the Medic Alert member wearing the bracelet has made available 
* the client displays the information to the emergency worker

# Server Identity 

Both Medic Alert New Zealand and Australia implement this web service. In addition, there is a test 
web server that can be used to access synthesised patient data. The actual server address is referred
to throughout this implementation as [server]. For the test server, the address is:

http://test.healthintersections.com.au/medicalert

# Security 

The medic alert server only responds to systems with a known and pre-registered SSL certificate installed
that identifies the client. Contact [to be provided] in order to register an SSL certificate to gain
access to the system. 

Note: the Medic Alert web servers grant different levels of trust to different certificates depending 
on their exposure to the public web. This will be discussed during the registration process.

**No certificate = no access to the web service**

In addition to the server, the end-user may also be identified. The end-user is identified by an openID
connect JWT in the HTTP header. Specifically, the JWT is presented as a Bearer token in the Authorization
header. This token identifies the end-user, and where appropriate arrangements have been made, the 
Medic Alert web service will trust the identity of the end-user. This is also discussed during SSL
certificate registration.

**No openID Bearer Token = access is treated as unknown user**

# Member Consent

As part of their enrollment and maintenance process, members choose to record a set of information about 
their healthcare with Medic Alert, and then choose how much of this information they wish to share with 
healthcare providers. 

Patients may choose to share some or all of their information with:
- emergency care providers (e.g. Ambulance officers)
- healthcare providers (doctors, nurses, healthcare information)
- any one at all

Note that the exact choices that members makes varies depending on jurisdiction and time, but all members make these kind of choices.

When responding to requests for information about members, the Medic Alert servers will consider the information provided by the client
(as described above in the Security section), and the choices made by the member, and only return what the patient has authorised to
release for the appropriate category. 

Some members may choose to release no information to 'any one at all', so any request for 
patient information which is not associated with known and trusted system and/or users 
will return a 404 Patient not found, even if the patient is a current (or past) member 
of Medic Alert.

# Getting Information about a patient 

There are 2 different ways to get information about a patient: as a set of separate RESTful access calls that assemble the information desired about the member, 
or as a single large request that returns everything that is available about the member. 

This implementation guide describes how to access each of the different information available, and then describes how to access all the information in a single
request.

# Patient Demographics and Contacts

~~~~~~~~
 GET [base]/Patient/[id]
~~~~~~~~

where id is found on the medic alert bracelet etc. This returns a Patient resource that contains the 
details available about the patient and their emergency contacts, or a 404 not found error. For further details, 
see [Member Details](StructureDefinition-Member.html)

# Additional details about the patient

If a patient record is returned, additional information is available about the patient. 
The following information is potentially available (depending on whether the member has recorded it and made it available):

<table>
 <tr><td>Allergies</td><td><code>GET [base]/AllergyIntolerance?patient=[id] </code></td><td>see <a href="StructureDefinition-Allergy.html">Allergy Details</a></td></tr>
 <tr><td>Obsevations</td><td><code>GET [base]/Observation?patient=[id] </code></td><td>see <a href="StructureDefinition-BloodGroup.html">Patient's Blood group</a></td></tr>
 <tr><td>Conditions</td><td><code>GET [base]/Condition?patient=[id]</code></td><td>see <a href="StructureDefinition-Condition.html">Conditions</a></td></tr>
 <tr><td>Surgical Procedures</td><td><code>GET [base]/Procedure?patient=[id]</code></td><td>see <a href="StructureDefinition-Procedure.html">Surgical Procedures</a></td></tr>
 <tr><td>Medications</td><td><code>GET [base]/MedicationStatement?patient=[id]</code></td><td>see <a href="StructureDefinition-Medication.html">Medications</a></td></tr>
 <tr><td>Devices</td><td><code>GET [base]/DeviceUseStatement?patient=[id]</code></td><td>see <a href="StructureDefinition-DeviceUse.html">Devices</a></td></tr>
 <tr><td>Warnings</td><td><code>GET [base]/Flag?patient=[id]</code></td><td>see <a href="StructureDefinition-MedicalWarning.html">Warnings</a></td></tr>
 <tr><td>Documents</td><td><code>GET [base]/DocumentReference?patient=[id]</code></td><td>see <a href="StructureDefinition-Document.html">Documents</a></td></tr>
 <tr><td>Doctor List</td><td><code>GET [base]/CareTeam?patient=[id]</code></td><td>see <a href="StructureDefinition-DoctorList.html">Doctor List</a></td></tr>
</table>

All of these requests return a Bundle - a FHIR resource that contains 
other resources. e.g. a list of resources of the described kind. If
an empty bundle is returned, the member has not recorded any relevant
information, or decided not to share it.

# Getting everything at once

The client can make a single query that returns all of the information that is available
for a patient. 

~~~~~~~~
 GET [base]/Patient/[id]/$everything
~~~~~~~~

This query returns the same information that would be returned by making each
of the queries above, in a single Bundle resource, though the order of the resources may vary.

# Push

It's also possible to set up a PUSH arrangement where the same information 
as in $everything is pushed to another database (e.g. the national MyHR). 
This is not yet described or implemented, but will be implemented using
the methods as developed by <http://wiki.hl7.org/index.php?title=201709_Consumer_Centered_Data_Exchange>.


