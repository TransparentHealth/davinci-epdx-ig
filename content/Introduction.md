# Da Vinci ePDx Implementation Guide
#davinci/ePDx/IG-1

| This is a pre-release version (Ballot 1) of ePayer Data Exchange  (ePDx) R1/STU. There is no current official version. | 

This specification is currently undergoing ballot and connectathon testing. It is expected to evolve, possibly significantly, as part of that process.

Feedback is welcome and may be submitted through the [FHIR gForge tracker](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677/) indicating “US Da Vinci ePDx” as the specification. If balloting on this IG, please submit your comments via the tracker and just reference them in your ballot submission implementation guide.

## 1.1 Introduction
The Da Vinci ePayer Data Exchange (ePDx) initiative is specifying the FHIR profiles that will be used to support interoperable communication from Payers to Providers and health plan members that a practitioner is caring for.

Whereas the Blue Button 2.0 initiative is specifying the profiles used to communicate between health plans and their members. The ePDx specification is focused on presenting member health and claims information available to the health plan in FHIR clinical profiles that are more easily handled by provider Electronic Medical Records (EMR) systems. Wherever possible, ePDx will use established US Core FHIR Profiles. Where information must be presented in FHIR resources that fall outside of the Argonaut/US Core implementation guides ePDx will define the necessary Da Vinci FHIR profiles to contain the relevant information.

The ePDx Implementation Guide (IG) will use the HL7 FHIR Release 4/US Core STU3 specification as it’s base, but will provide additional guidance and documentation to support implementations that follow the HL7 FHIR STU3/US Core STU2 and HL7 FHIR DSTU2/Argonaut specifications. 

The ePDx profiles documented in this IG will be used to transmit data to provider systems. The mechanism used for this interaction will be based upon the CDS-Hooks specification.  Providers will be able to initiate a request for information to a health plan as part of their normal workflows. The CDS-Hooks interface will be used to pass information about the Patient. This information will be used to match the patient to the Health Plans member records and return relevant claims and associated health information to the provider’s EMR using appropriate FHIR clinical resources.

## 1.2 Supporting Specifications
This implementation guide is dependent on other specifications. Please submit any comments you have on these base specifications as follows:

* Feedback on CDS Hooks should be posted to the CDS Hooks [GitHub Issue List](https://github.com/cds-hooks/docs/issues)
* Feedback on the FHIR core specification should be submitted to the [FHIR gForge tracker](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) with "FHIR Core" as the specification.
* Feedback on the US core profiles should be submitted to the [FHIR gForge tracker](http://gforge.hl7.org/gf/project/fhir/tracker/?action=TrackerItemAdd&tracker_id=677) with "US Core" as the specification.
* Individuals interested in participating in ePayer Data Exchange (ePDx) or other HL7 Da Vinci projects can find information about Da Vinci [here](http://www.hl7.org/about/davinci).

There are a few places in this implementation guide marked as ‘ToDo’. All such areas represent supplementary content such as examples, additional background or context or other non-definitional content. I.e. they do not change any of the conformance expectations on implementers. Where ToDo appears, such content will be created and included in the implementation guide prior to publication as a Standard for Trial Use.

## 1.3 ePDx Profiles
The ePDx profiles that can be made available to a provider are listed below:
	- Patient
	- Condition 
	- Medication 
	- MedicationStatement 
	- Allergy Intolerance 
	- Procedure 
	- Device 
	- Immunization 
	- DocumentReference 
	- Observation 
	- Practitioner 
	- PractitionerRole 
	- Organization 
	- Location
	- Encounter 
	- Coverage 
	- Provenance
	- HealthcareService

## 1.4 Derived Profiles
From the above listed profiles the following use the US Core STU3 Profiles:
### FHIR R4/US Core STU3 Profiles
	- [US Core Patient Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-patient.html)
	- [US Core Condition Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-condition.html)
	- [US Core Medication Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-medication.html)
	- [US Core MedicationStatement Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-medicationstatement.html)
	- [US Core AllergyIntolerance Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-allergyintolerance.html)
	- [US Core Procedure Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-procedure.html)
	- [US Core Device Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-device.html)
	- [US Core Immunization Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-immunization.html)
	- [US Core DocumentReference Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-documentreference.html)
	- [US Core ObservationResults Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-observationresults.html)
	- [US Core Practitioner Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-practitioner.html)
	- [US Core PractitionerRole Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-practitionerrole.html)
	- [US Core Organization Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-organization.html)
	- [US Core Location Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-location.html)
	- [US Core Encounter Profile](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-encounter.html)

### 1.5 Da Vinci ePDx Profiles

The following profiles do not have a defined profile in US Core therefore these are Da Vinci specific profiles:
	- Coverage
	- Provenance
	- HealthcareService

## 1.6 Extensions
The ePDx IG uses extensions defined in the [US Core IG](http://hl7.org/fhir/us/core/2019Jan/profiles.html#extensions):
	- [US Core Race Extension](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-race.html)
	- [US Core Ethnicity Extension](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-ethnicity.html)
	- [US Core Birth Sex Extension](http://hl7.org/fhir/us/core/2019Jan/StructureDefinition-us-core-birthsex.html). 

In cases where Health Plans do not have a record of Birth Sex the field will be assigned the “UNK/Unknown”  [NullFlavor](http://build.fhir.org/v3/NullFlavor/cs.html).

## 2.1 CDS Hooks
Sharing of member health information via ePDx will use the CDS Hooks specification. Connection to health plan systems will be supported via the following hooks:
	- Patient-view
	- Medication-Prescribe

Information will be returned embedded in “Suggestion Cards”. This will enable the data to be accepted by the provider and populated into the EMR as part of the patient record.


