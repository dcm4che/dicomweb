## DICOMWeb Worklist Services (UPS-RS) - (HL7/DICOM Austria Jahrestagung 2024)

### Timeline of DICOM Specifications of Workflow Services
- 1993: [ACR-NEMA PS 3.4-1993: Detached Patient/Study/Results Management Service Classes](https://dicom.nema.org/medical/dicom/1992-1995/PS3.4_1993.pdf)
- 1993: [Supp 10: Basic Worklist Management - Modality](https://dicom.nema.org/medical/dicom/Final/sup09_ft.pdf)) 
- 1996: [Supp 17: Modality Performed Procedure Step](https://dicom.nema.org/medical/dicom/Final/sup17_ft.pdf)
- 2000: [Supp 52: General Purpose Worklist](https://dicom.nema.org/medical/dicom/Final/sup52_ft.pdf)
- 2004: [Supp 98: Retirement of Detached, Standalone and other Services](https://dicom.nema.org/medical/dicom/Final/sup98_ft.pdf)
- 2009: [Supp 96: Unified Worklist and Procedure Step](https://dicom.nema.org/medical/dicom/Final/sup96_ft.pdf)
- 2011: [Supp 158: Retirement of General Purpose Worklist and Procedure Step](https://dicom.nema.org/medical/dicom/Final/sup158_ft.pdf)
- 2014: [Supp 171: Unified Procedure Step by REpresentational State Transfer (REST) Services](https://dicom.nema.org/medical/dicom/Final/sup171_ft2.pdf)

### [Unified Procedure Step IOD (Information Object Definition) Modules](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_B.26.2.html)

- [SOP Common Module](#sop-common-module)
- [Unified Procedure Step Relationship Module](#unified-procedure-step-relationship-module)
- [Unified Procedure Step Scheduled Procedure Information Module](#unified-procedure-step-scheduled-procedure-information-module)
- [Unified Procedure Step Progress Information Module](#unified-procedure-step-progress-information-module)
- [Unified Procedure Step Performed Procedure Information Module](#unified-procedure-step-performed-procedure-information-module)
- [Patient Demographic Module](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_C.2.3.html) (optional)
- [Patient Medical Module](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_C.2.4.html) (optional)
- [Visit Identification Module](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_C.3.2.html) (optional)
- [Visit Status Module](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_C.3.3.html) (optional)
- [Visit Admission Module](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_C.3.4.html) (optional)

#### [SOP Common Module](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_C.12.html#sect_C.12.1)

| Attribute Name         | Tag         | Attribute Description                                                                          |
|------------------------|-------------|------------------------------------------------------------------------------------------------|
| Specific Character Set | (0008,0005) | Character Set that expands or replaces the Basic Graphic Set.                                  |
| SOP Class UID          | (0008,0016) | Uniquely identifies the Unified Procedure Step - Push SOP Class: `1.2.840.10008.5.1.4.34.6.1`. |
| SOP Instance UID       | (0008,0018) | Uniquely identifies the SOP Instance.                                                          |
| ..                     | ..          | ..                                                                                             |

#### [Unified Procedure Step Relationship Module](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_C.30.4.html)

| Attribute Name                    | Tag         | Attribute Description                                                                           |
|-----------------------------------|-------------|-------------------------------------------------------------------------------------------------|
| Patient's Name                    | (0010,0010) | Patient's full legal name.                                                                      |
| Patient ID                        | (0010,0020) | Primary identifier for the patient.                                                             |
| Referenced Request Sequence       | (0040,A370) | Requested Procedures to which the Procedure Step contributes.                                   |
| \>Study Instance UID              | (0020,000D) | Unique identifier for the Study.                                                                |
| \>Accession Number                | (0008,0050) | A departmental Information System generated number that identifies the Imaging Service Request. |
| \>Requested Procedure ID          | (0040,1001) | Identifier of the related Requested Procedure.                                                  |
| \>Requested Procedure Description | (0032,1060) | Institution-generated description or classification of the Requested Procedure.                 |
| Replaced Procedure Step Sequence  | (0074,1224) | Canceled procedure step(s) that are replaced by this procedure step.                            |
| \>Referenced SOP Class UID        | (0008,1150) | Uniquely identifies the Unified Procedure Step - Push SOP Class: `1.2.840.10008.5.1.4.34.6.1`.  |
| \>Referenced SOP Instance UID     | (0008,1155) | Uniquely identifies the referenced SOP Instance.                                                |
| ..                                | ..          | ..                                                                                              |

#### [Unified Procedure Step Scheduled Procedure Information Module](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_C.30.2.html)

| Attribute Name                                      | Tag         | Attribute Description                                                                                                               |
|-----------------------------------------------------|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Scheduled Procedure Step Priority                   | (0074,1200) | Priority of the scheduled Procedure Step: `HIGH`, `MEDIUM` or `LOW`.                                                                |
| Scheduled Procedure Step Modification Date and Time | (0040,4010) | Date and time when the Scheduled Procedure Information was last modified or first created (whichever is most recent).               |
| Worklist Label                                      | (0074,1202) | A label identifying the worklist to which the Procedure Step Instance belongs.                                                      |
| Procedure Step Label                                | (0074,1204) | A label describing the task of the Procedure Step in text appropriate for displaying in the user selection interface.               |
| Scheduled Workitem Code Sequence                    | (0040,4018) | Coded description of the Procedure Step.                                                                                            |
| \>Code Value                                        | (0008,0100) | The identifier of the Coded Entry.                                                                                                  |
| \>Coding Scheme Designator                          | (0008,0102) | The identifier of the coding scheme in which the Coded Entry is defined.                                                            |
| \>Code Meaning                                      | (0008,0104) | Text that conveys the meaning of the Coded Entry.                                                                                   |
| Scheduled Processing Parameters Sequence            | (0074,1210) | Processing parameters to be used by the performing system when carrying out the Procedure Step.                                     |
| \>_Include Content Item Macro Attributes_           |             | [Coded Concept Name + Typed Value](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_10.2.html#table_10-2)      |
| Scheduled Station Name Code Sequence                | (0040,4025) | Identifying names within the enterprise of the equipment for which the Procedure Step is scheduled.                                 |
| \>Code Value                                        | (0008,0100) | The identifier of the Coded Entry.                                                                                                  |
| \>Coding Scheme Designator                          | (0008,0102) | The identifier of the coding scheme in which the Coded Entry is defined.                                                            |
| \>Code Meaning                                      | (0008,0104) | Text that conveys the meaning of the Coded Entry.                                                                                   |
| Scheduled Station Class Code Sequence               | (0040,4026) | Classes of the equipment for which the Procedure Step is scheduled.                                                                 |
| \>Code Value                                        | (0008,0100) | The identifier of the Coded Entry.                                                                                                  |
| \>Coding Scheme Designator                          | (0008,0102) | The identifier of the coding scheme in which the Coded Entry is defined.                                                            |
| \>Code Meaning                                      | (0008,0104) | Text that conveys the meaning of the Coded Entry.                                                                                   |
| Scheduled Station Geographic Location Code Sequence | (0040,4027) | Geographic locations of the equipment for which the Procedure Step is scheduled.                                                    |
| \>Code Value                                        | (0008,0100) | The identifier of the Coded Entry.                                                                                                  |
| \>Coding Scheme Designator                          | (0008,0102) | The identifier of the coding scheme in which the Coded Entry is defined.                                                            |
| \>Code Meaning                                      | (0008,0104) | Text that conveys the meaning of the Coded Entry.                                                                                   |
| Scheduled Human Performers Sequence                 | (0040,4034) | Human performers that are scheduled to be involved or responsible for performing the Procedure Step.                                |
| \>Human Performer Code Sequence                     | (0040,4009) | Human performer that is involved or responsible for performing the Procedure Step.                                                  |
| \>>Code Value                                       | (0008,0100) | The identifier of the Coded Entry.                                                                                                  |
| \>>Coding Scheme Designator                         | (0008,0102) | The identifier of the coding scheme in which the Coded Entry is defined.                                                            |
| \>>Code Meaning                                     | (0008,0104) | Text that conveys the meaning of the Coded Entry.                                                                                   |
| Scheduled Procedure Step Start DateTime             | (0040,4005) | Date and time at which the Procedure Step is scheduled to start.                                                                    |
| Expected Completion DateTime                        | (0040,4011) | Date and time at which the Procedure Step  is expected to be completed.                                                             |
| Scheduled Procedure Step Expiration DateTime        | (0040,4008) | Date and time after which the Procedure Step is meaningless or undesirable.                                                         |
| Input Readiness State                               | (0040,4034) | Readiness state of the Input Information Sequence (0040,4021) and the referenced Instances. `INCOMPLETE`, `UNAVAILABLE` or `READY`. |
| Input Information Sequence                          | (0040,4021) | References to Information Objects needed to perform the scheduled Procedure Step.                                                   |
| \>Type of Instances                                 | (0040,E020) | Type of object Instances referenced. `DICOM`, `CDA`, ..                                                                             |
| \>Study Instance UID                                | (0020,000D) | Unique identifier for the Study.                                                                                                    |
| \>Series Instance UID                               | (0020,000E) | Unique identifier for the Unique identifier for the Series that is part of the Study identified in Study Instance UID (0020,000D).  |
| \>Referenced SOP Sequence                           | (0008,1199) | References to object Instances.                                                                                                     |
| \>>Referenced SOP Class UID                         | (0008,1150) | Uniquely identifies the referenced SOP Class.                                                                                       |
| \>>Referenced SOP Instance UID                      | (0008,1155) | Uniquely identifies the referenced SOP Instance.                                                                                    |
| \>DICOM Retrieval Sequence                          | (0040,E021) | Details for retrieving Instances via the DICOM Retrieve Service.                                                                    |
| \>>Retrieve AE Title                                | (0008,0054) | Title of a DICOM Application Entity where the referenced Instance(s) may be retrieved on the network.                               |
| \>WADO Retrieval Sequence                           | (0040,E023) | Details for retrieving Instances available via WADO-URI.                                                                            |
| \>>Retrieve URI                                     | (0040,E010) | URI/URL specifying the location of the referenced Instance(s).                                                                      |
| \>XDS Retrieval Sequence                            | (0040,E024) | Details for retrieving Instances using the IHE XDS-I.b RAD-69 Transaction.                                                          |
| \>>Repository Unique ID                             | (0040,E030) | Uniquely identifies a Repository from which the referenced Instances can be retrieved.                                              |
| \>>Home Community ID                                | (0040,E031) | Uniquely identifies a Community to which requests for the referenced Instances can be directed.                                     |
| \>WADO-RS Retrieval Sequence                        | (0040,E025) | Details for retrieving Instances via WADO-RS.                                                                                       |
| \>>Retrieve URL                                     | (0008,1190) | URL specifying the location of the referenced Instance(s).                                                                          |
| Study Instance UID                                  | (0020,000D) | Unique Study identification that shall be used for the created Composite SOP Instances resulting from this Unified Procedure Step.  |
| Output Destination Sequence                         | (0040,4070) | The destination to which the performer is requested to store the output objects generated.                                          |
| \>Referenced SOP Class UID                          | (0008,1150) | Required if the storage request only applies to a specific SOP Class.                                                               |
| \>DICOM Storage Sequence                            | (0040,4071) | Details for retrieving Instances via the DICOM Retrieve Service.                                                                    |
| \>>Destination AE                                   | (2100,0140) | Title of a DICOM Application Entity to which Instances will be stored.                                                              |
| \>STOW-RS Storage Sequence                          | (0040,4072) | Details for storing Instances via STOW-RS.                                                                                          |
| \>>Storage URL                                      | (0040,4073) | URI/URL specifying the location of the STOW-RS storage service to which Instances will be stored.                                   |
| \>XDS Storage Sequence                              | (0040,4074) | Details for storing Instances via the IHE Provide and Register Document Set-b (ITI-41) transaction.                                 |
| \>>Repository Unique ID                             | (0040,E030) | Uniquely identifies a Repository.                                                                                                   |
| \>>Home Community ID                                | (0040,E031) | Uniquely identifies a Community.                                                                                                    |
| ..                                                  | ..          | ..                                                                                                                                  |

#### [Unified Procedure Step Progress Information Module](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_C.30.html#sect_C.30.1)

| Attribute Name                               | Tag         | Attribute Description                                                                                                       |
|----------------------------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------|
| Procedure Step State                         | (0074,1000) | State of the Procedure Step. `SCHEDULED`, `IN PROGRESS`, `CANCELED` or `COMPLETED`.                                         |
| Progress Information Sequence                | (0074,1002) | Information about work progress for the Procedure Step.                                                                     |
| \>Procedure Step Progress                    | (0074,1004) | A numerical indicator of progress expressed as percentage complete.                                                         |
| \>Procedure Step Progress Description        | (0074,1006) | A textual description of progress.                                                                                          |
| \>Procedure Step Communications URI Sequence | (0074,1008) | Contact Information to communicate with performers of the Procedure Step.                                                   |
| \>>Contact URI                               | (0074,100A) | URI to communicate with performer of the procedure in progress.                                                             |
| \>>Contact Display Name                      | (0074,100C) | Name of the person, department or organization to contact for more information about the performance of the Procedure Step. |
| \>Procedure Step Cancellation DateTime       | (0040,4052) | Date and Time at which the procedure step was discontinued.                                                                 |
| \>Reason For Cancellation                    | (0074,1238) | A textual description of the reason a procedure step was discontinued.                                                      |
| ..                                           | ..          | ..                                                                                                                          |

#### [Unified Procedure Step Performed Procedure Information Module](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_C.30.3.html)

| Attribute Name                                        | Tag         | Attribute Description                                                                                                              |
|-------------------------------------------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------|
| Unified Procedure Step Performed Procedure Sequence   | (0074,1216) | Details of the Procedure Step as performed.                                                                                        |
| \>Performed Workitem Code Sequence                    | (0040,4019) | A Sequence that conveys the type of procedure performed.                                                                           |
| \>>Code Value                                         | (0008,0100) | The identifier of the Coded Entry.                                                                                                 |
| \>>Coding Scheme Designator                           | (0008,0102) | The identifier of the coding scheme in which the Coded Entry is defined.                                                           |
| \>>Code Meaning                                       | (0008,0104) | Text that conveys the meaning of the Coded Entry.                                                                                  |
| \>Performed Processing Parameters Sequence            | (0074,1212) | Parameters used to perform the procedure.                                                                                          |
| \>>_Include Content Item Macro Attributes_            |             | [Coded Concept Name + Typed Value](https://dicom.nema.org/medical/dicom/current/output/chtml/part03/sect_10.2.html#table_10-2)     |
| \>Performed Station Name Code Sequence                | (0040,4028) | Names within the enterprise of the equipment that performed the Procedure Step.                                                    |
| \>>Code Value                                         | (0008,0100) | The identifier of the Coded Entry.                                                                                                 |
| \>>Coding Scheme Designator                           | (0008,0102) | The identifier of the coding scheme in which the Coded Entry is defined.                                                           |
| \>>Code Meaning                                       | (0008,0104) | Text that conveys the meaning of the Coded Entry.                                                                                  |
| \>Performed Station Class Code Sequence               | (0040,4029) | Classes of the equipment that created the Procedure Step.                                                                          |
| \>>Code Value                                         | (0008,0100) | The identifier of the Coded Entry.                                                                                                 |
| \>>Coding Scheme Designator                           | (0008,0102) | The identifier of the coding scheme in which the Coded Entry is defined.                                                           |
| \>>Code Meaning                                       | (0008,0104) | Text that conveys the meaning of the Coded Entry.                                                                                  |
| \>Performed Station Geographic Location Code Sequence | (0040,4030) | Geographic locations of the equipment that created Procedure Step.                                                                 |
| \>>Code Value                                         | (0008,0100) | The identifier of the Coded Entry.                                                                                                 |
| \>>Coding Scheme Designator                           | (0008,0102) | The identifier of the coding scheme in which the Coded Entry is defined.                                                           |
| \>>Code Meaning                                       | (0008,0104) | Text that conveys the meaning of the Coded Entry.                                                                                  |
| \>Actual Human Performers Sequence                    | (0040,4035) | Human performers that are/were actually involved or responsible for performing the Procedure Step.                                 |
| \>>Human Performer Code Sequence                      | (0040,4009) | Human performer that is involved or responsible for performing the Procedure Step.                                                 |
| \>>>Code Value                                        | (0008,0100) | The identifier of the Coded Entry.                                                                                                 |
| \>>>Coding Scheme Designator                          | (0008,0102) | The identifier of the coding scheme in which the Coded Entry is defined.                                                           |
| \>>>Code Meaning                                      | (0008,0104) | Text that conveys the meaning of the Coded Entry.                                                                                  |
| \>Performed Procedure Step Start DateTime             | (0040,4050) | Date and Time at which the Procedure Step started.                                                                                 |
| \>Performed Procedure Step End DateTime               | (0040,4051) | Date and Time at which the Procedure Step ended.                                                                                   |
| \>Output Information Sequence                         | (0040,4033) | References to information created as part of the Procedure Step.                                                                   |
| \>>Type of Instances                                  | (0040,E020) | Type of object Instances referenced. `DICOM`, `CDA`, ..                                                                            |
| \>>Study Instance UID                                 | (0020,000D) | Unique identifier for the Study.                                                                                                   |
| \>>Series Instance UID                                | (0020,000E) | Unique identifier for the Unique identifier for the Series that is part of the Study identified in Study Instance UID (0020,000D). |
| \>>Referenced SOP Sequence                            | (0008,1199) | References to object Instances.                                                                                                    |
| \>>>Referenced SOP Class UID                          | (0008,1150) | Uniquely identifies the referenced SOP Class.                                                                                      |
| \>>>Referenced SOP Instance UID                       | (0008,1155) | Uniquely identifies the referenced SOP Instance.                                                                                   |
| \>>DICOM Retrieval Sequence                           | (0040,E021) | Details for retrieving Instances via the DICOM Retrieve Service.                                                                   |
| \>>>Retrieve AE Title                                 | (0008,0054) | Title of a DICOM Application Entity where the referenced Instance(s) may be retrieved on the network.                              |
| \>>WADO Retrieval Sequence                            | (0040,E023) | Details for retrieving Instances available via WADO-URI.                                                                           |
| \>>>Retrieve URI                                      | (0040,E010) | URI/URL specifying the location of the referenced Instance(s).                                                                     |
| \>>XDS Retrieval Sequence                             | (0040,E024) | Details for retrieving Instances using the IHE XDS-I.b RAD-69 Transaction.                                                         |
| \>>>Repository Unique ID                              | (0040,E030) | Uniquely identifies a Repository from which the referenced Instances can be retrieved.                                             |
| \>>>Home Community ID                                 | (0040,E031) | Uniquely identifies a Community to which requests for the referenced Instances can be directed.                                    |
| \>>WADO-RS Retrieval Sequence                         | (0040,E025) | Details for retrieving Instances via WADO-RS.                                                                                      |
| \>>>Retrieve URL                                      | (0008,1190) | URL specifying the location of the referenced Instance(s).                                                                         |
| ..                                                    | ..          | ..                                                                                                                                 |

### [Unified Procedure Step Service and SOP Classes (DIMSE Service)](https://dicom.nema.org/medical/dicom/current/output/html/part04.html#chapter_CC)

Defines 4 different SOP Classes bundling usage specific combinations of operations:

- [Unified Procedure Step - **Push** SOP Class](#unified-procedure-step-push-sop-class)
- [Unified Procedure Step - **Pull** SOP Class](#unified-procedure-step-pull-sop-class)
- [Unified Procedure Step - **Watch** SOP Class](#unified-procedure-step-watch-sop-class)
- [Unified Procedure Step - **Event** SOP Class](#unified-procedure-step-event-sop-class)
- [Unified Procedure Step - **Query** SOP Class](#unified-procedure-step-query-sop-class)
 
#### Unified Procedure Step - Push SOP Class

  | Operation (DIMSE)             | Usage SCU/SCP |
  |-------------------------------|---------------|
  | Create UPS (N-CREATE)         | M/M           |
  | Request UPS Cancel (N-ACTION) | U/M           |
  | Get UPS Information (N-GET)   | U/M           |

#### Unified Procedure Step - Pull SOP Class

  | Operation (DIMSE)           | Usage SCU/SCP |
  |-----------------------------|---------------|
  | Search for UPS (C-FIND)     | M/M           |
  | Get UPS Information (N-GET) | M/M           |
  | Update UPS (N-SET)          | M/M           |
  | Change UPS State (N-ACTION) | M/M           |


  To take control of a `SCHEDULED` UPS, an SCU shall generate a Transaction UID and submit a state change to `IN PROGRESS`
  including the Transaction UID in the submission. The SCU shall record and use the Transaction UID in future N-ACTION
  and N-SET requests for that UPS instance.

  | Attribute Name  | Tag         | Description                                                          |
  |-----------------|-------------|----------------------------------------------------------------------|
  | Transaction UID | (0008,1195) | UID to lock the UPS instance for getting processed by another actor. |

#### Unified Procedure Step - Watch SOP Class

  | Operation (DIMSE)                                | Usage SCU/SCP |
  |--------------------------------------------------|---------------|
  | Un/Subscribe to Receive Event Reports (N-ACTION) | M/M           |
  | Get UPS Information (N-GET)                      | M/M           |
  | Search fo UPS (C-FIND)                           | U/M           |
  | Request UPS Cancel (N-ACTION)                    | U/M           |

  An SCU may Subscribe/Unsubscribe to Receive UPS Event Reports
  - for an individual UPS instance
  - for all UPS instances ("Global Subscription")
  - for a subset of UPS instances matching specified keys ("Filtered Global Subscription")

  To subscribe to Receive UPS Event Reports, the N-ACTION SCU has to specify

  | Attribute Name | Tag         | Attribute Description                                                                             |
  |----------------|-------------|---------------------------------------------------------------------------------------------------|
  | Receiving AE   | (0074,1234) | AE Title of the N-EVENT-REPORT SCU to which UPS Event Reports shall be sent.                      |
  | Deletion Lock  | (0074,1230) | Indicates if `COMPLETED` or `CANCELED` UPS instances shall **not** be deleted. `TRUE` or `FALSE`. |

#### Unified Procedure Step - Event SOP Class

  | Operation (DIMSE)                              | Usage SCU/SCP |
  |------------------------------------------------|---------------|
  | Report a Change in UPS Status (N-EVENT-REPORT) | M/M           |

  Event Types:

  | Event Type Name      | Trigger                                                                                                                                                                                                                                                       |
  |----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | UPS State Report     | - new UPS instance created <br> - change of _Procedure Step State (0074,1000)_ <br> - change of _Input Readiness State (0040,4041)_                                                                                                                           |
  | UPS Cancel Requested | receive Request UPS Cancel (N-ACTION)                                                                                                                                                                                                                       |
  | UPS Assigned         | - new UPS instance created <br> - change of _Scheduled Station Name Code Sequence (0040,4025)_ <br> - change of _Scheduled Human Performers Sequence (0040,4034)_                                                                                             |
  | UPS Progress Report  | - change of _Procedure Step Progress (0074,1004)_ <br> - change of _Procedure Step Progress Description (0074,1006)_ <br> - change of _Procedure Step Communications URI Sequence (0074,1008)_                                                                |
  | SCP Status Change    | restart of the SCP, specifying <br> - _SCP Status (0074,1242)_: `GOING DOWN` or `RESTARTED` <br> - _Subscription List Status (0074,1244)_: `WARM START` or `COLD START` <br> - _Unified Procedure Step List Status (0074,1246)_: `WARM START` or `COLD START` |

#### Unified Procedure Step - Query SOP Class

  | Operation (DIMSE)      | Usage SCU/SCP |
  |------------------------|---------------|
  | Search fo UPS (C-FIND) | M/M           |
