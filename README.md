### DICOMweb

[DICOMWeb - Wikipedia](https://en.wikipedia.org/wiki/DICOMweb)
> DICOMweb is a term applied to the family of RESTful DICOM services defined for sending, retrieving and querying for
> medical images and related information.
>
> The intent is to provide a light-weight mobile device and web browser friendly mechanism for accessing images, which
> can be implemented by developers who have minimal familiarity with the DICOM standard and which uses consumer
> application friendly mechanisms like http, JSON and media types (like "image/jpeg") to the maximum extent possible.

**Corresponding DICOM Upper Layer (DUL) - also referenced as DIMSE - services**

DICOMweb | DUL/DIMSE service
-- | --
[Studies Service Store Transaction (STOW-RS)](https://dicom.nema.org/medical/dicom/current/output/html/part18.html#sect_10.5) | [Storage Service Class (C-STORE)](https://dicom.nema.org/medical/dicom/current/output/html/part04.html#chapter_B)
[Studies Service Search Transaction (QIDO-RS)](https://dicom.nema.org/medical/dicom/current/output/html/part18.html#sect_10.6) | [Study Root Query/Retrieve Information Model - FIND SOP Class](https://dicom.nema.org/medical/dicom/current/output/html/part04.html#sect_C.4.1)
[Studies Service Store Transaction (WADO-RS)](https://dicom.nema.org/medical/dicom/current/output/html/part18.html#sect_10.4) | [Study Root Query/Retrieve Information Model - GET SOP Class](https://dicom.nema.org/medical/dicom/current/output/html/part04.html#sect_C.4.3)
[Worklist Service (UPS-RS)](https://dicom.nema.org/medical/dicom/current/output/html/part18.html#chapter_11) | [Unified Procedure Step Service and SOP Classes](https://dicom.nema.org/medical/dicom/current/output/html/part04.html#chapter_CC)

[Introduction of DICOMweb Services at NEMA](https://www.dicomstandard.org/using/dicomweb)

### History
- 2003: [Supp 85: Web Access to DICOM Objects (WADO)](https://dicom.nema.org/medical/dicom/Final/sup85_ft.pdf)
- 2010: [Medical Imaging Network Transport (MINT)](https://studylib.net/doc/5441544/mint-conformance---medical-imaging-network-transport)
- 2011: [Supp 148: Web Access to DICOM Persistent Objects by Means of Web Services Extension of the Retrieve Service (WADO Web Service)](https://dicom.nema.org/medical/dicom/Final/sup161_ft.pdf)
- 2011: [Supp 161: WADO by means of RESTful Services](https://dicom.nema.org/medical/dicom/Final/sup161_ft.pdf)
- 2011: [Supp 163: Store Over the Web by RESTful Services (STOW-RS)](https://dicom.nema.org/medical/dicom/Final/sup163_ft3.pdf)
- 2011: [Supp 166: Query based on ID for DICOM Objects by RESTful Services (QIDO-RS)](https://dicom.nema.org/medical/dicom/Final/sup166_ft5.pdf)
- 2014: [Supp 171: Unified Procedure Step by REpresentational State Transfer (REST) Services](https://dicom.nema.org/medical/dicom/Final/sup172_ft2.pdf)
- 2015: [Supp 174: RESTful Rendering](https://dicom.nema.org/medical/dicom/Final/sup174_ft.pdf)
- 2016: [Supp 194: RESTful Services for Non-Patient Instances](https://dicom.nema.org/medical/dicom/Final/sup194_ft.pdf)
- 2017: [Supp 198: Retirement of WADO-WS](https://dicom.nema.org/medical/dicom/Final/sup198_ft2_retire_wado-ws.pdf)
- 2019: [Supp 183: PS3.18 Web Services Re-Documentation](https://dicom.nema.org/medical/dicom/Final/sup183_ft_part18_redoc.pdf)
(Made specification hard to read by use of extended Augmented Backus-Naur Form (ABNF) notation and introduced several
inconsistency with [previous PS3.18 2019a](https://dicom.nema.org/medical/dicom/2019a/output/html/part18.html) by
incorrect extractions of "Common Aspects of DICOM Web Services" from previous individual service descriptions.)
- 2020: [Supp 203: Thumbnail Resources for DICOMweb](https://dicom.nema.org/medical/dicom/Final/sup203_ft_Thumbnail_Resources_for_DICOMweb.pdf)
- 2020: [Supp 228: DICOMweb API for Server Volumetric Rendering](https://www.dicomstandard.org/News-dir/ftsup/docs/sups/sup228.pdf)
- 2021: [CP 2040 DICOMweb DICOM Media Types and Bulkdata Endpoints](https://dicom.nema.org/medical/dicom/Final/cp2040_ft_DICOMwebMediaTypes_and_BulkDataEndpoints.pdf)
- ????: [Supp 211: DICOMweb Support for Retrieve via application/zip](https://dicom.nema.org/medical/dicom/Supps/LB/sup211_lb_zip_archive.pdf)

### [QIDO-RS](https://petstore.swagger.io/index.html?url=https://dcm4che.github.io/dicomweb/openapi.json#/QIDO-RS)

Examples:
```console
$ curl -v -H 'Accept: application/dicom+json' 'http://localhost:8080/dcm4chee-arc/aets/DCM4CHEE/rs/studies?PatientName=Zeta%5E%2A&StudyDate=20220928'
*   Trying 127.0.0.1:8080...
* Connected to localhost (127.0.0.1) port 8080 (#0)
> GET /dcm4chee-arc/aets/DCM4CHEE/rs/studies?PatientName=Zeta%5E%2A&StudyDate=20220928 HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.81.0
> Accept: application/dicom+json
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Cache-Control: no-cache
< Access-Control-Allow-Headers: origin, content-type, accept, authorization
< Access-Control-Expose-Headers: content-type, warning
< Date: Sun, 12 Mar 2023 15:25:53 GMT
< Connection: keep-alive
< Access-Control-Allow-Origin: *
< Access-Control-Allow-Credentials: true
< Transfer-Encoding: chunked
< Content-Type: application/dicom+json
< Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS, HEAD
< 
[{"00080005":{"vr":"CS"},"00080020":{"vr":"DA","Value":["20220928"]},"00080030":{"vr":"TM","Value":["214137.000"]},"00080050":{"vr":"SH"},"00080054":{"vr":"AE","Value":["DCM4CHEE"]},"00080056":{"vr":"CS","Value":["ONLINE"]},"00080061":{"vr":"CS","Value":["SM"]},"00080090":{"vr":"PN"},"00080201":{"vr":"SH"},"00081190":{"vr":"UR","Value":["http://localhost:8080/dcm4chee-arc/aets/DCM4CHEE/rs/studies/2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604"]},"00100010":{"vr":"PN","Value":[{"Alphabetic":"Zeta^Zachary"}]},"00100020":{"vr":"LO","Value":["ccbaf3d29596b6d2"]},"00100030":{"vr":"DA","Value":["19830606"]},"00100040":{"vr":"CS","Value":["M"]},"0020000D":{"vr":"UI","Value":["2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604"]},"00200010":{"vr":"SH","Value":["Case-F"]},"00201206":{"vr":"IS","Value":["1"]},"00201208":{"vr":"IS","Value":["1"]}}]$ curl -vH 'Accept: application/dicom+json' 'http://localhost:8080/dcm4chee-arc/aets/DCM4CHEE/rs/studies?PatientName=Zeta%5E%2A&StudyDate=20220928'
```

```console
$ curl -v -H 'Accept: multipart/related; type="application/dicom+xml"' 'http://localhost:8080/dcm4chee-arc/aets/DCM4CHEE/rs/studies?00100010=Zeta%5E%2A&00080020=20220928'
*   Trying 127.0.0.1:8080...
* Connected to localhost (127.0.0.1) port 8080 (#0)
> GET /dcm4chee-arc/aets/DCM4CHEE/rs/studies?00100010=Zeta%5E%2A&00080020=20220928 HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.81.0
> Accept: multipart/related; type="application/dicom+xml"
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Cache-Control: no-cache
< Access-Control-Allow-Headers: origin, content-type, accept, authorization
< Access-Control-Expose-Headers: content-type, warning
< Date: Sun, 12 Mar 2023 15:28:40 GMT
< Connection: keep-alive
< Access-Control-Allow-Origin: *
< Access-Control-Allow-Credentials: true
< Transfer-Encoding: chunked
< Content-Type: multipart/related;start="<fdb89c06-15e4-45cc-a9b2-2e48ba0d8ed0@resteasy-multipart>";type="application/dicom+xml"; boundary=31a077d1-31cc-4c93-9190-0a5c98661f38
< Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS, HEAD
< 
--31a077d1-31cc-4c93-9190-0a5c98661f38
Content-ID: <fdb89c06-15e4-45cc-a9b2-2e48ba0d8ed0@resteasy-multipart>
Content-Type: application/dicom+xml

<?xml version="1.0" encoding="UTF-8"?><NativeDicomModel xml:space="preserve"><DicomAttribute keyword="SpecificCharacterSet" tag="00080005" vr="CS"/><DicomAttribute keyword="StudyDate" tag="00080020" vr="DA"><Value number="1">20220928</Value></DicomAttribute><DicomAttribute keyword="StudyTime" tag="00080030" vr="TM"><Value number="1">214137.000</Value></DicomAttribute><DicomAttribute keyword="AccessionNumber" tag="00080050" vr="SH"/><DicomAttribute keyword="RetrieveAETitle" tag="00080054" vr="AE"><Value number="1">DCM4CHEE</Value></DicomAttribute><DicomAttribute keyword="InstanceAvailability" tag="00080056" vr="CS"><Value number="1">ONLINE</Value></DicomAttribute><DicomAttribute keyword="ModalitiesInStudy" tag="00080061" vr="CS"><Value number="1">SM</Value></DicomAttribute><DicomAttribute keyword="ReferringPhysicianName" tag="00080090" vr="PN"/><DicomAttribute keyword="TimezoneOffsetFromUTC" tag="00080201" vr="SH"/><DicomAttribute keyword="RetrieveURL" tag="00081190" vr="UR"><Value number="1">http://localhost:8080/dcm4chee-arc/aets/DCM4CHEE/rs/studies/2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604</Value></DicomAttribute><DicomAttribute keyword="PatientName" tag="00100010" vr="PN"><PersonName number="1"><Alphabetic><FamilyName>Zeta</FamilyName><GivenName>Zachary</GivenName></Alphabetic></PersonName></DicomAttribute><DicomAttribute keyword="PatientID" tag="00100020" vr="LO"><Value number="1">ccbaf3d29596b6d2</Value></DicomAttribute><DicomAttribute keyword="PatientBirthDate" tag="00100030" vr="DA"><Value number="1">19830606</Value></DicomAttribute><DicomAttribute keyword="PatientSex" tag="00100040" vr="CS"><Value number="1">M</Value></DicomAttribute><DicomAttribute keyword="StudyInstanceUID" tag="0020000D" vr="UI"><Value number="1">2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604</Value></DicomAttribute><DicomAttribute keyword="StudyID" tag="00200010" vr="SH"><Value number="1">Case-F</Value></DicomAttribute><DicomAttribute keyword="NumberOfStudyRelatedSeries" tag="00201206" vr="IS"><Value number="1">1</Value></DicomAttribute><DicomAttribute keyword="NumberOfStudyRelatedInstances" tag="00201208" vr="IS"><Value number="1">1</Value></DicomAttribute></NativeDicomModel>
--31a077d1-31cc-4c93-9190-0a5c98661f38--
```

Remarks:
- QIDO-RS defines paging by _Query Parameters_ `offset` and `limit`, but only specifies that the list of returned matches
shall be ordered, but not by which criteria!
- QIDO-RS **always** applies _combined date and time Range Matching_ if values of date **and** time of a DA/TM attribute
pair (e.g. Study Date/Time) are passed as _Query Attributes_; in contrast to the
_Study Root Query/Retrieve Information Model - FIND SOP Class_ where separate (independent) Range Matching of date and
time Attributes is applied by default (= without [extended Negotion of _combined date and time Range Matching_](https://dicom.nema.org/medical/dicom/current/output/html/part04.html#sect_C.5.1.1)).


### [DICOM JSON Format](https://dicom.nema.org/medical/dicom/current/output/html/part18.html#chapter_F)

-> [Example](dicom.json)

### [DICOM XML Format](https://dicom.nema.org/medical/dicom/current/output/html/part19.html#sect_A.1)

-> [Example](dicom.xml)

### [WADO-URI](https://petstore.swagger.io/index.html?url=https://dcm4che.github.io/dicomweb/openapi.json#/WADO-URI)

Examples:

Retrieve Rendered DICOM Image:
```console
$ curl -v -o out 'http://localhost:8080/dcm4chee-arc/aets/DCM4CHEE/wado?requestType=WADO&studyUID=2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604&seriesUID=2.16.840.1.113995.3.110.3.0.10118.6000009.258169&objectUID=2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1'
*   Trying 127.0.0.1:8080...
* Connected to localhost (127.0.0.1) port 8080 (#0)
> GET /dcm4chee-arc/aets/DCM4CHEE/wado?requestType=WADO&studyUID=2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604&seriesUID=2.16.840.1.113995.3.110.3.0.10118.6000009.258169&objectUID=2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1 HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.81.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Access-Control-Allow-Headers: origin, content-type, accept, authorization
< Access-Control-Expose-Headers: content-type, warning
< Date: Sun, 12 Mar 2023 19:56:15 GMT
< Connection: keep-alive
< Access-Control-Allow-Origin: *
< ETag: "-888292472"
< Last-Modified: Fri, 10 Mar 2023 10:25:19 GMT
< Access-Control-Allow-Credentials: true
< Transfer-Encoding: chunked
< Content-Type: image/jpeg
< Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS, HEAD
< 
{ [16392 bytes data]
```

Retrieve compressed DICOM Part 10 file:
```console
$ curl -v -o out 'http://localhost:8080/dcm4chee-arc/aets/DCM4CHEE/wado?requestType=WADO&studyUID=2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604&seriesUID=2.16.840.1.113995.3.110.3.0.10118.6000009.258169&objectUID=2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1&contentType=application/dicom&transferSyntax=*'
*   Trying 127.0.0.1:8080...
> GET /dcm4chee-arc/aets/DCM4CHEE/wado?requestType=WADO&studyUID=2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604&seriesUID=2.16.840.1.113995.3.110.3.0.10118.6000009.258169&objectUID=2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1&contentType=application/dicom&transferSyntax=* HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.81.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Access-Control-Allow-Headers: origin, content-type, accept, authorization
< Access-Control-Expose-Headers: content-type, warning
< Date: Sun, 12 Mar 2023 20:07:57 GMT
< Connection: keep-alive
< Access-Control-Allow-Origin: *
< ETag: "-888292472"
< Last-Modified: Fri, 10 Mar 2023 10:25:19 GMT
< Access-Control-Allow-Credentials: true
< Transfer-Encoding: chunked
< Content-Type: application/dicom;transfer-syntax=1.2.840.10008.1.2.4.50
< Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS, HEAD
< 
{ [18418 bytes data]
```

### [WADO-RS](https://petstore.swagger.io/index.html?url=https://dcm4che.github.io/dicomweb/openapi.json#/WADO-RS)

Examples:

Retrieve compressed DICOM Part 10 file:
```console
$ curl -v -o out 'http://localhost:8080/dcm4chee-arc/aets/DCM4CHEE/rs/studies/2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604/series/2.16.840.1.113995.3.110.3.0.10118.6000009.258169/instances/2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1'
*   Trying 127.0.0.1:8080...
> GET /dcm4chee-arc/aets/DCM4CHEE/rs/studies/2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604/series/2.16.840.1.113995.3.110.3.0.10118.6000009.258169/instances/2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1 HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.81.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Access-Control-Allow-Headers: origin, content-type, accept, authorization
< Access-Control-Expose-Headers: content-type, warning
< Date: Sun, 12 Mar 2023 20:31:20 GMT
< Connection: keep-alive
< Access-Control-Allow-Origin: *
< ETag: "-888292472"
< Last-Modified: Fri, 10 Mar 2023 10:25:19 GMT
< Access-Control-Allow-Credentials: true
< Transfer-Encoding: chunked
< Content-Type: multipart/related;start="<1e5b6b38-6fb4-4ba5-824c-e627cc8194ef@resteasy-multipart>";transfer-syntax=1.2.840.10008.1.2.4.50;type="application/dicom"; boundary=9d056d4f-1f1a-4488-9760-581378378090
< Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS, HEAD
< 
{ [16392 bytes data]
* Connection #0 to host localhost left intact
```
```console
$ head -n5 out
--9d056d4f-1f1a-4488-9760-581378378090
Content-ID: <1e5b6b38-6fb4-4ba5-824c-e627cc8194ef@resteasy-multipart>
Content-Type: application/dicom;transfer-syntax=1.2.840.10008.1.2.4.50

DICMUL�OBUI1.2.840.10008.5.1.4.1.1.77.1.6UI22.16.840.1.113995.3.110.3.0.10118.6000009.258169.1UI1.2.840.10008.1.2.4.50UI1.2.40.0.13.1.3SHdcm4che-5.29CS DERIVED\PRIMARY\VOLUME\RESAMPLED2022101TM
```

Retrieve Rendered DICOM Image:
```console
$ curl -v -o out 'http://localhost:8080/dcm4chee-arc/aets/DCM4CHEE/rs/studies/2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604/series/2.16.840.1.113995.3.110.3.0.10118.6000009.258169/instances/2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1/rendered'
*   Trying 127.0.0.1:8080...
> GET /dcm4chee-arc/aets/DCM4CHEE/rs/studies/2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604/series/2.16.840.1.113995.3.110.3.0.10118.6000009.258169/instances/2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1/rendered HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.81.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Access-Control-Allow-Headers: origin, content-type, accept, authorization
< Access-Control-Expose-Headers: content-type, warning
< Date: Sun, 12 Mar 2023 20:34:50 GMT
< Connection: keep-alive
< Access-Control-Allow-Origin: *
< ETag: "-888292472"
< Last-Modified: Fri, 10 Mar 2023 10:25:19 GMT
< Access-Control-Allow-Credentials: true
< Transfer-Encoding: chunked
< Content-Type: image/jpeg
< Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS, HEAD
< 
{ [49176 bytes data]
* Connection #0 to host localhost left intact
```

Retrieve Metadata of DICOM Object
```console
$ curl -v -H 'Accept: application/dicom+json' 'http://localhost:8080/dcm4chee-arc/aets/DCM4CHEE/rs/studies/2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604/series/2.16.840.1.113995.3.110.3.0.10118.6000009.258169/instances/2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1/metadata'
*   Trying 127.0.0.1:8080...
* Connected to localhost (127.0.0.1) port 8080 (#0)
> GET /dcm4chee-arc/aets/DCM4CHEE/rs/studies/2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604/series/2.16.840.1.113995.3.110.3.0.10118.6000009.258169/instances/2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1/metadata HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.81.0
> Accept: application/dicom+json
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Access-Control-Allow-Headers: origin, content-type, accept, authorization
< Access-Control-Expose-Headers: content-type, warning
< Date: Sun, 12 Mar 2023 20:43:25 GMT
< Connection: keep-alive
< Access-Control-Allow-Origin: *
< ETag: "-888292472"
< Last-Modified: Fri, 10 Mar 2023 10:25:19 GMT
< Access-Control-Allow-Credentials: true
< Transfer-Encoding: chunked
< Content-Type: application/dicom+json
< Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS, HEAD
< 
[{"00080008":{"vr":"CS","Value":["DERIVED","PRIMARY","VOLUME","RESAMPLED"]},"00080012":{"vr":"DA","Value":["20221012"]},"00080013":{"vr":"TM","Value":["033156.000"]},"00080016":{"vr":"UI","Value":["1.2.840.10008.5.1.4.1.1.77.1.6"]},"00080018":{"vr":"UI","Value":["2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1"]},"00080020":{"vr":"DA","Value":["20220928"]},"00080023":{"vr":"DA","Value":["20221012"]},"0008002A":{"vr":"DT","Value":["20220928214137.000"]},"00080030":{"vr":"TM","Value":["214137.000"]},"00080033":{"vr":"TM","Value":["033157.285"]},"00080050":{"vr":"SH","Value":["MODIFIED"]},"00080060":{"vr":"CS","Value":["SM"]},"00080070":{"vr":"LO","Value":["Roche Tissue Diagnostics"]},"00080090":{"vr":"PN"},"00080201":{"vr":"SH"},"00081090":{"vr":"LO","Value":["VENTANA DP 600"]},"00089206":{"vr":"CS","Value":["VOLUME"]},"00100010":{"vr":"PN","Value":[{"Alphabetic":"Zeta^Zachary"}]},"00100020":{"vr":"LO","Value":["ccbaf3d29596b6d2"]},"00100021":{"vr":"LO","Value":["DCM4CHEE.BAAD35D6.0BD17C2F"]},"00100022":{"vr":"CS","Value":["TEXT"]},"00100030":{"vr":"DA","Value":["19830606"]},"00100040":{"vr":"CS","Value":["M"]},"00181000":{"vr":"LO","Value":["6000009"]},"0018100B":{"vr":"UI","Value":["2.16.840.1.113995.3.110.3.10118"]},"00181020":{"vr":"LO","Value":["100979-d6b9803","0092"]},"0020000D":{"vr":"UI","Value":["2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604"]},"0020000E":{"vr":"UI","Value":["2.16.840.1.113995.3.110.3.0.10118.6000009.258169"]},"00200010":{"vr":"SH","Value":["Case-F"]},"00200011":{"vr":"IS","Value":["1"]},"00200013":{"vr":"IS","Value":["1"]},"00200052":{"vr":"UI","Value":["2.16.840.1.113995.3.110.3.0.10118.6000009.258169.0.1"]},"00201040":{"vr":"LO","Value":["SLIDE_CORNER"]},"00209221":{"vr":"SQ","Value":[{"00209164":{"vr":"UI","Value":["2.16.840.1.113995.3.110.3.0.10118.6000009.258169.0.2"]}}]},"00209311":{"vr":"CS","Value":["TILED_FULL"]},"00280002":{"vr":"US","Value":[3]},"00280004":{"vr":"CS","Value":["YBR_FULL_422"]},"00280006":{"vr":"US","Value":[0]},"00280008":{"vr":"IS","Value":["1"]},"00280010":{"vr":"US","Value":[1280]},"00280011":{"vr":"US","Value":[1280]},"00280100":{"vr":"US","Value":[8]},"00280101":{"vr":"US","Value":[8]},"00280102":{"vr":"US","Value":[7]},"00280103":{"vr":"US","Value":[0]},"00280301":{"vr":"CS","Value":["NO"]},"00282110":{"vr":"CS","Value":["01"]},"00282112":{"vr":"DS","Value":["10"]},"00282114":{"vr":"CS","Value":["ISO_10918_1"]},"00400512":{"vr":"LO","Value":["PV22;ROC;Case-F;Slide-F-5"]},"00400513":{"vr":"SQ"},"00400518":{"vr":"SQ","Value":[{"00080100":{"vr":"SH","Value":["433466003"]},"00080102":{"vr":"SH","Value":["SCT"]},"00080104":{"vr":"LO","Value":["Microscope Slide"]}}]},"00400555":{"vr":"SQ"},"00400560":{"vr":"SQ","Value":[{"00400551":{"vr":"LO","Value":["PV22;ROC;Case-F;Slide-F-5"]},"00400554":{"vr":"UI","Value":["2.16.840.1.113995.3.110.3.0.10118.6000009.114392"]},"00400562":{"vr":"SQ"},"00400610":{"vr":"SQ"}}]},"00480001":{"vr":"FL","Value":[14.878604888916016]},"00480002":{"vr":"FL","Value":[25.200210571289062]},"00480003":{"vr":"FL","Value":[0.0010000000474974513]},"00480006":{"vr":"UL","Value":[520]},"00480007":{"vr":"UL","Value":[880]},"00480008":{"vr":"SQ","Value":[{"0040072A":{"vr":"DS","Value":["5.989978"]},"0040073A":{"vr":"DS","Value":["30.823605"]}}]},"00480010":{"vr":"CS","Value":["NO"]},"00480011":{"vr":"CS","Value":["AUTO"]},"00480012":{"vr":"CS","Value":["NO"]},"00480102":{"vr":"DS","Value":["1","0","0","0","-1","0"]},"00480105":{"vr":"SQ","Value":[{"00220016":{"vr":"SQ","Value":[{"00080100":{"vr":"SH","Value":["111744"]},"00080102":{"vr":"SH","Value":["DCM"]},"00080104":{"vr":"LO","Value":["Brightfield illumination"]}}]},"00282000":{"vr":"OB","BulkDataURI":"http://localhost:8080/dcm4chee-arc/aets/DCM4CHEE/rs/studies/2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604/series/2.16.840.1.113995.3.110.3.0.10118.6000009.258169/instances/2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1/bulkdata/00480105/0/00282000"},"00480106":{"vr":"SH","Value":["1"]},"00480108":{"vr":"SQ","Value":[{"00080100":{"vr":"SH","Value":["414298005"]},"00080102":{"vr":"SH","Value":["SCT"]},"00080104":{"vr":"LO","Value":["Full Spectrum"]}}]}}]},"00480302":{"vr":"UL","Value":[1]},"00480303":{"vr":"UL","Value":[1]},"22000002":{"vr":"UT"},"22000005":{"vr":"LT","Value":["PV22;ROC;Case-F;Slide-F-5"]},"52009229":{"vr":"SQ","Value":[{"00081140":{"vr":"SQ"},"00289110":{"vr":"SQ","Value":[{"00180050":{"vr":"DS","Value":["0.001000"]},"00280030":{"vr":"DS","Value":["0.029760","0.029760"]}}]},"00400710":{"vr":"SQ","Value":[{"00089007":{"vr":"CS","Value":["DERIVED","PRIMARY","VOLUME","RESAMPLED"]}}]}}]},"7FE00010":{"vr":"OB","BulkDataURI":"http://localhost:8080/dcm4chee-arc/aets/DCM4CHEE/rs/studies/2.16.840.1.113995.3.110.3.0.10118.6000009.497166.721604/series/2.16.840.1.113995.3.110.3.0.10118.6000009.258169/instances/2.16.840.1.113995.3.110.3.0.10118.6000009.258169.1"}}]
```

### [STOW-RS](https://petstore.swagger.io/index.html?url=https://dcm4che.github.io/dicomweb/openapi.json#/STOW-RS)

Examples:
```

```


### [UPS-RS](https://petstore.swagger.io/index.html?url=https://dcm4che.github.io/dicomweb/openapi.json#/UPS-RS)

TODO
