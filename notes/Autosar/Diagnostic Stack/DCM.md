- NRC's
- Access to NV mem is implemented specific and has to be ensured during integration
- Serves for external diagnostic tool in between communication manager (ex. read DTC's from [[DEM]] and giving it to external tool)
- Errors in logic/autosar violations is detected by [[DET]]
- Communicates via ports+port Interfaces with [[PDUR]] and contains Routing Table for PDU's

## DSL
- Session handling
- ASW timings
- Response behaivour (to PDUR from DSD and vice versa)
- State handling
- Tester Present logic
- ROE transmission, segmented response, ResponsePending
- Track of non-default sessions
- Diagnostic protocols + resource managment
- Full,Silent,NoCom
- Buffer config for Rx/Tx
- PDU table

## DSD
- Security + Session access (0x7F NRC)
- Positive/Negative/Suppressed response
- SID Table (adding to response from DSP to DSL)

## DSP

- Response assembling and verification
- Subfunction check and message format
- Response with no SID
- Service implementation
- NRC handling
- Sender/Receiver communication

##### DID configuration
1) **Individual DID** with one connection per configured data element of respective DID. Interface DataServices should be used. Configured in *DcmDspDid*. If DID refers to other DID, it needs to be configured in *DcmDspDidReference*, *DcmDspDidSignal* for reference and position data in diagnostic response/rquest. *DcmDspData* container has following info:
	- DcmDspDidIdentifier
	- DcmDspDidByteOffset
	- DcmDspDidDataReference
	- DcmDspDataByteSize
	- DcmDspDataType
	- DcmDspDataUsePort
	- DcmDspDataWriteFunction
	- DcmDspReadFucntion
2) **Range DID** configuration, used to handle set of DID's sharing same behaivour in one SWC, with one port connection. Interface DataServices_DIDRange_{Range} should be used. Can be limited in functionality by *DcmDspDidInfo*
*Parametres for DID configuration*:
- DcmDspDIDRangeLowerLimit
- DcmDspDIDRangeUpperLimit
- DcmDspDIDRangeMaxDataLength
- DcmDspDIDRangeHasGaps

#### Routine Control (Sid 0x31)
Used to perform custom function withing ECU
![[Pasted image 20230608110654.png]]
For Routine execution exist pre-conditions:
	- Engine should not run
	- OEM specific
	- Vehicle should not move
	- Immobilizer should be unlocked
	- etc
Three subfunctions: 01 Start Routine ; 02 Stop Routine ; 03 Request Result Routine
01 Start Routine -- if resp pos it will add (01 - routine running ; 02 - routine is finished successfully ; 03 - failed N_OK ; 04 - Stopped)