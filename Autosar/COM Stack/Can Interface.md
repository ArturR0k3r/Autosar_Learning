- HOH's (HRH/HTH)
- **Interrupt** (relevant CanIf services is called withing corresponding ISR in CanDrv when If. gets notified by Drv of interrupt occuring) / **Polling** (In this case Can_MainFunction_() must be called periodically within a defined time interval. CanIf is notified by [[Can Drv]] about events (Reception, Transmission, BusOff, Timeout), that occurred in one of the CAN Controllers, equally to the interrupt driven operation.) / **Mixed**
- Basic/Full Can
- Routing Table for PDU's (for [[PDUR]])
- Filtering by appling mask and checking with mask
- Support dynamic PDU's (reconfiguration of CanID during runtime)
- Data Length + pointer to data buffer for function providing Tx/Rx
- Controlling CAN Tranceiver
- State of bus: aviability of bus for transmission (NoCom,Silent,FullCom)
- Alive presence + addition of nodes + wake up/shutdown
- Unpacking/Packing PDU's (L-PDU = L-SDU + DLC + ID)
- Data transmission mode (local buffering/directly transmitting on bus)
- Data flow (Normal/Triggered)

![Pasted image 20230606164237](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/8059dc3a-7d47-486c-9946-83004eedb30b)
