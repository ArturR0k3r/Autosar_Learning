<h1>What is Memory Stack</h1>

![Pasted image 20230809111624](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/c9fce6ac-80b6-43a1-8256-1395888e6bc6)

To manage Non Volatile (NV) memory in automotive domain  Memory Stack (MemStack) is used in AUTOSAR environment. MemStack in AUTOSAR deals with :  

 **1. Storage of data in non NV memory, in structured manner.**  
 **2. To read stored data from NV memory. To write Data into NV memory**  
 **3. Provides abstraction, to access internal or external NV memory.**  
 **4. Managing memory write cycles to ensure endurance of NV memory.**  
 **5. Managing error correction and error detection mechanisms for NV memory**.  
 **6. Management of Memory blocks.**  
 **7. Address mapping : Virtual to Physical address mapping**.  

**Memory stack (MemStack) of AUTOSAR provides services to application layer and BSW modules to access Non volatile memory** (e.g read and write NV memory). Using AUTOSAR MemStack APIs, software components (SWCs) in application layer and BSW modules can read data from NV memory and write data to NV memory, **e.g. DEM uses services of MemStack to write freeze frame data into memory.**

The NVM accesses the module MEMIF (Memory Abstraction Interface) which abstracts the modules FEE (Flash EEPROM Emulation) and EA (EEPROM Abstraction). Thus, the NVM is hardware independent.Applications normally do not access the services of the BSW modules directly. They use the service ports provided by the BSW modules via the RTE.  
  
Application SWC or NV SWC can read/write data from/to NV memory. These SWC are connected to NVRAM manager by service ports. Using service provided by NVRAM manager SWCs communicate with NVRAM manager to read/write data from/ to memory, then NVRAM manager passes call to Memory interface and then call goes to Memory driver module then driver module writes data to NV memory. In case of external NV memory (connected via SPI), SPI drivers will be used.  
  

To write a data in memory SWC initiates command to write i.e. uses RTE call, call will pass from from RTE to NV memory : 

RTE--> NVRAM Manager --> MemIf-->FEE-->FLS-->NV Memory

RTE--> NVRAM Manager --> MemIf-->Ea-->Eep-->NV Memory

<h2>Beware! For more specific information, watch videos and read either docs from official site either from sources provided in corresponding file</h2>

###  NVRAM Manager

NV RAM manager or NvM module, **provides services for data storage and data maintenance**. NvM module present in service layer of AUTOSAR stack and provides services to user (i.e. SWCs) to read data from or write data to NV memory. NV RAM manager is only way to access memory or we can say a gateway to access NV memory for SWCs.  
  
NV RAM manager performs initialization of memory, error correction and error detection of NV block. 

###  Memory Abstraction Interface (MemIf) :

MemIf module provides abstraction from underlying FEE or EA  modules, so upper layer module e.g. NVRAM manager will requests to MemIf module for read/write operation and MemIf module will pass request to underlying FEE or EA module.  
  
**FEE and EA provides virtual 32 bit address space and abstracts device specific addressing scheme**. FEE and EA converts virtual address to physical address.

###  Memory Driver :

**Memory driver used to access micro-controllers memory.** Memory driver provides reading, writing and erasing to and from EEPROM or Flash memory. FLS driver is associated with Flash memory and EEP driver associated with EEPROM memory.  
  
A driver for an external EEPROM uses handlers (SPI in most cases) or drivers to access the external EEPROM device. It is located in the ECU Abstraction Layer.
