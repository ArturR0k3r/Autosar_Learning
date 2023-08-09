- Contains PDU Routing Table (Id's for each PDU)
- Gateway interaction with [[COM]] and [[DCM]] 
- Calculates unique path by oncoming PDU and destination to which it headed
- Ways of transmitting PDU:
	1) Upper module calls *PduR_\<Up>Transmit()* function
	2) Lower communication interface request transmission by using *PduR_\<Lo>TriggerTransmit* and PDUR routes call to *PduR_\<Up>TriggerTransmit*, data is copied by upper module
	3) Coping data offer *PduR_\<Up>Transmit* when lower layers calls *PduR_\<Lo>TriggerTransmit*
- Gateway for 1 protocol
- Data transmission can be done directly on coming, or copied in local buffer
- Aviability to cancel of transmission/receiption
- Global buffers(all routing paths that are not referenced) / dedicated buffers (routing paths that are referenced, for fast high prio OBD requests)
- Buffering strategies depends on *PduRQueueDepth* (if > 0 => FIFO queue aviable and it has states)
- Do not checks length of I-PDU
- Support receiption of buffer