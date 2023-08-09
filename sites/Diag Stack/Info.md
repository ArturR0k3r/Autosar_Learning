<h1>What is Diagnostic Stack</h1>
![[Pasted image 20230809110515.png]]
Vehicle diagnostics is all about checking the health of your vehicle using some protocols. Protocols are either on board vehicle diagnostics (OBD) protocol or off board protocols (UDS). Using these protocols information from different systems or sensors can be read or error reported by ECUs can be read and error related data can be read and many more things can be done using diagnostics
**NvM is part of memory stack**. **Here NvM is required to store event related data when event fails.** i.e. to store **freeze frame** data and extended data. Blocks are created in NvM to store diagnostic event related data

<h2>Beware! For more specific information, watch videos and read either docs from official site either from sources provided in corresponding file</h2>
### Diagnostic Event Manager (DEM)

DEM is present at system service layer in AUTOSAR architecture module. DEM module is responsible for processing diagnostic events and storing event and event related data to NvM. Also DEM provides diagnostics information to DCM module i.e. DTC status or snapshot data (freeze-frame). 
  
DEM modules defines DTCs (Diagnostics Trouble Codes). DTCs are associated to events (e.g. event of sensor fault) and SWC (Monitor function which monitors sensor state) or BSW modules (Monitor function of BSW module which monitors state of BSW modules) can report event status (Passed or Failed) to DEM module i.e. in case if event fails **DEM module will set DTC status bytes as per ISO-14229** **and request /NvM to store Event and event related data to NvM
### Diagnostic Communication Manager (DCM)

DCM is present at Communication Service layer in AUTOSAR architecture module. DCM is part of diagnostic stack. DCM is responsible for communication between external testing tool **(used for requesting diagnostic data from ECU using services provided by ISO 14229)**. Data may be DTC status or to read DID values. 

**DCM module accepts incoming request service from tester tool validates service and take proper action related to service** (it may communicate to DEM for reading DTC related info) and send **Positive response** or **Negative Response Code (NRCs)** based on validation of incoming request and processing of request.

Format of request and response is defined in ISO 14229.
### Development Error Tracer (DET)

DET is module is used at time of development. While Development DET module is enabled and for final release DET should be disabled. **DET module provides APIs to report an error.** **When DET module is enabled, different checks are added to functions of different BSW modules to capture an error**. **Error are API function is called with wrong argument, API function is called with NULL Pointer etc. Each error has an error number** and each module has a module number.  
  
More information about DET error code for each BSW module is defined in respective SWS document provided by Autosar.  
  
### Function Inhibition Monitor (FIM)

FIM module responsible for inhibition of particular functionality of software components based on event status. FIM used FID (Function Identifier). FID represents functionality with inhibition condition. There is an inhibition condition and if particular inhibition condition is satisfied respective functionality will be stopped from execution. FID is assigned to SWC.  
  
 An event is assigned to FID. Based on event status FID's status is derived and which will decide whether to execute functionality or not.