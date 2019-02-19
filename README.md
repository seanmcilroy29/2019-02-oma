# 2019-02-oma

Meeting information and materials for the February 2019 phone call with OMA SpecWorks DMSE and IPSO working groups.

Time: 2019-02-26 8:00-10:00 PST (17:00-19:00 CET)

## Draft Agenda

* Introductions 
* [CoAP Observe](https://tools.ietf.org/html/rfc7641): observations across security context changes
* [CoRE Dynlink](https://tools.ietf.org/html/draft-ietf-core-dynlink-07): LwM2M use alignment
* [CoRE Resource Directory](https://tools.ietf.org/html/draft-ietf-core-resource-directory-19): recent changes and their effect on LwM2M
* [SenML FETCH/PATCH](https://tools.ietf.org/html/draft-ietf-core-senml-etch-00): Read-Composite and Write-Composite with FETCH/PATCH
* [URNs for Device Identifiers](https://tools.ietf.org/html/draft-ietf-core-dev-urn-03): LwM2M use alignment
* Data types and encodings
 
## Call-in info

TBD

## Meeting minutes

Etherpad: https://etherpad.tools.ietf.org/p/notes-t2trg-oma-20190226

## Agenda details 

### CoAP Observe
 
LwM2M need to maintain observation across security contexts. If DTLS session between LwM2M client and server changes for any reason, existing observations on the device could be maintained instead of requiring to re-send all the observations to the client. The reason behind this is also how LwM2M correlates the authorization of the client with the DTLS session and requires the client to re-register if the DTLS session changes, causing all observations to be re-sent.

### CoRE Dynlink

Better alignment with CoRE dynlink.
 
* Sending notifications for transition above/below gt and lt are currently different between LwM2M and dynlink. Introducing "band" to LwM2M might be a solution.

* What value should be sent after [pmin expires](http://www.openmobilealliance.org/release/LightweightM2M/V1_1-20180612-C/OMA-TS-LightweightM2M_Core-V1_1-20180612-C.html#5-1-2-0-512-Attributes-Classification)? The value that 1) "would have caused notification", 2) "the value right after pmin expires", 3) something else, or 4) potentially nothing if the conditions for the notification no longer apply. Seems to depend how pmin is used. If it's used to avoid debounce notifications, 4 seems appropriate. For catching relevant values 1 seems good. More details in Dynlink draft needed?

### CoRE Resource Directory

Recent changes in the RD draft and their effect on LwM2M.
 
### SenML FETCH/PATCH

* POST vs. PATCH in LwM2M: What are the implications if we replace POST with PATCH for [partial update](http://www.openmobilealliance.org/release/LightweightM2M/V1_1-20180612-C/OMA-TS-LightweightM2M_Core-V1_1-20180612-C.html#6-3-3-0-633-Write) or keep them both or don’t change at all?

* SenML FETCH/PATCH status and Read-Composite and Write-Composite LwM2M use. New media types needed to avoid context-aware processing.

### URNs for Device Identifiers

LwM2M uses dev-URNs for [Endpoint Client Names](http://www.openmobilealliance.org/release/LightweightM2M/V1_1-20180612-C/OMA-TS-LightweightM2M_Core-V1_1-20180612-C.html#7-3-1-0-731-Endpoint-Client-Name). Do we have all cases covered or is further alignment needed?

### Data types and encodings

* Planned new data types for LwM2M
* Using CBOR for efficient encoding of resource values
