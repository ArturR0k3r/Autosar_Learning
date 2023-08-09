- Packing/Unpacking signals PDU to transmit
- Providing unpacked signals to [[RTE]]
- Gateway signaling (received signals of ipdu -> ipdu to be transmited ex. getting CAN signal and packing it in FR msg) + 1:n
- Communication transmission control (start/stop of I-PDU groups)
- Minimum distances between transmit I-PDU's
- Signals timeout
- Endiannes conversion and sign extension (2's compliment)
- Init values for signals
- Fills in unused areaas in a frame with *CinTxIPduUnusedAreasDefault*
- Filtering out the received signals values via filter algorithms
	![Pasted image 20230607104614](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/5c5bc7f1-be9f-4941-bbf8-438dcfcff129)

- Containing Routing Table for [[PDUR]]
- Key factors for transmitting a frame are *ComTransferPropery*(TRIGGERED, TRIGGERED_WITHOUT_REPETION, TRIGGERED_ON_CHANGE, TRIGGERED_ON_CHANGE_WITHOUT_REPETITION, PENDING), *ComFilterAlgorithm*, *ComTxModeMode*(Direct,Periodic,Mixed,Non for PDU's), *TransmissionModeSelection*
	1) TRIGGERED - Request for transmission is triggered immediately and requested for value present in *ComTxModeNumberOfRepetitions* times
	2) TRIGGERED_WITHOUT_REPETITION - same but no repetition
	3) TRIGGERED_ON_CHANGE - If new sent signal differs to the already stored then transmission request is given and transmission request is repeated
	4) TRIGGER_ON_CHANGE_WITHOUT_REPETITION - ...
	5) PENDING - Request for transmission is given periodically
- **TMC** and **TMS** (Transmission mode Condition / Transmission mode Selection):
	Because an I-PDU can contain more than one signal, in the following, a method is defined to derive the I-PDU’s transmission mode from the state of the signals that are contained in one specific I-PDU.
	
	Two way of transmitting frame: True mode / False mode for TMS. 
	
	Values in *ComFilter* container is used as input for TMC based on which TMS is selected
	
	If *ComFilterAlgorithm* in *ComFilter* container configured as ALWAYS then no need of TMS configuration for FALSE case
	
	Basically dependent on True/False mode we can configure how I-PDU's will be treated for transmission
	![Pasted image 20230607120515](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/586e378a-5ee8-46ef-953e-ed309aedd8dd)

	
	![Pasted image 20230607122451](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/60bf4e67-9ee2-44ce-af6f-1d1df1a3e9fb)

	
	![Pasted image 20230607122735](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/bb86c75a-37ae-4a62-bde2-8b4e0e850ecf)
- If invalid signal is received COM informs upper layer about this invalid receiption
	If invalid value is received there are two types of action: Notify/Replace. Tag name : *ComDataInvalidAction*
	Depending of configuration it can notify via *ComInvalidNotification* function or replace it with what configured in *ComSignalInitValue*
- Callback of receiption can be Immediate or Deffered. Immediate - instantly informs RTE with receiption. Deffered it will set flag, that will be checked periodically and if what will be read by RTE
- Deadline monitoring can be disabled by *ComTimeout* = 0/omitted or by calling API Com_ReceptionDMControl()
	If in Rx deadline nothing comes, COM can proceed 3 ways: REPLACE, SUBSTITUTE, NONE that are configed in *ComReceivedDataTimeoutAction*
- Apart from IPDU buffer COM has shadow buffer that is used by group signals
	ex: /*Copy a to shadow buffer*/ Com_SendSignal(signal_a, &a);
	/*Copy b to shadow buffer*/ Com_SendSignal(signal_b, &b);
	/*Copy shadow buffer to IPDU*/ Com_SendSignalGroup(group_x);
- Update bit - idetify whether sender has updated the data in this signal or signal group. Could reside in anyy IPDU data
- IPDU callout functions - for debugging
