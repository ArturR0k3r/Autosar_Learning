- Indicates aviability (Tx/Rx posibility) of a specific bus communication to SWC.
- [[EcuM]] indicates to ComM wether communication is allowed or not.
- There are three comm modes: Full,Silent,NoCom; Silent is just used for synch shutdown. Default state - NoCom. Stores aviability in bool flag for all supported channels.
- FullCom has 2 states: Network Requested and Ready Sleep. In NoCom also 2 states: NoPendingRequest and RequestPending
- *CommunicationAllowed* flag can be set/reset only in NoCom state
- In SilentCom bus is prepring to sleep, and if there will be user requsts COMM_FULL_COMMUNICATION or ComM_DCM_ActiveDiagnostic, state machine will switch to FullCom
- Supports 4 shutdown synch variants configurable
	Only variant FULL and PASSIVE guarantees a synched shutdown between all nodes
	Synch shutdown not possible with LIGHT variant thus the ECU may continuously restart ("toggle") because of a msg from a node shutting down later
	ComM shall omit to call Nm_NetworkRequest() if configuration param is passive
	![Pasted image 20230607140522](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/c4d68e1b-360b-42de-a23a-8710488e3bc0)
- If any error in bus then SWC will provide inhibition request to ComM (Inhibition - mechanism to prevent other ECUs to wake up)
	If there is non-reliable wakeup source ECU should not send frames to other ECU. If it does, ECU will think as passive wakeup which will cause erroneous wakeup
- Partial Network Cluster (PNC) - one ECU support many PNC and their status is echanged via nm user data, and for each PNC ComM implements state machine. PNC existance is configurable.
