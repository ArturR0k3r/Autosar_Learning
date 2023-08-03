<h1>What is CAN?</h1>

**CAN** stands for "Controller Area Network," and it is a communication protocol used in the automotive and industrial sectors to facilitate communication between various electronic devices within a vehicle or industrial system.

CAN allows multiple electronic control units (ECUs) or nodes to communicate with each other over a single twisted-pair bus, using a differential signaling method to reduce electromagnetic interference. This protocol has become the standard in modern vehicles for interconnecting ECUs responsible for various tasks, such as engine control, transmission control, braking, airbags, infotainment systems, and more.

The key features of CAN include:

1. Multi-master communication: CAN allows multiple nodes to transmit and receive data simultaneously, creating a decentralized and flexible communication system. All nodes listens all info on bus and at the same time transmits info.

2. Message-based communication: Data on the CAN bus is transmitted in the form of messages, each containing an identifier and payload. This structure allows for efficient and reliable data exchange.

3. Deterministic communication: CAN is designed to be predictable and deterministic, meaning that messages are prioritized, and the system can guarantee a specific response time for critical messages.

4. Error detection and fault tolerance: CAN employs robust error-checking mechanisms, such as cyclic redundancy checks (CRC), to detect errors in transmitted data. It also has the ability to automatically recover from errors.

<h3>Physical Layer of CAN</h3>
How nodes(ECU's connected to CAN BUS) look like:

![NodesOnCan](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/5781da89-959a-4cfe-ac95-f0e5c0aaccbc)

Why we need tranceiver?
Controller (MCU) understands only logical 1 (high) or 0 (low), while CAN BUS works on differential signaling principle, so in the middle we have logical unit called tranceiver. Basically what tranceiver does is, it's connecting to bus, gets current voltages, performs them into logical 1/0, transmits them to controller, same in otger way.

Differential signaling principe:
High speed:
![Diff signal](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/b6c4817b-7425-4d24-a639-6aaea4c3bf53)
Low speed:
![Diff signal low](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/7e8424d2-aec8-4441-b590-6a6e754529db)
Why dominant? If on bus one ECU will transmit logical 1 and other will transmit logical 0, the state on bus will be 0 (dominant state), and 1 will be ommited.

Why twisted pair is one of the cases of e2e protection:
![Twisted pair](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/8d86043d-84b4-436c-8612-65069bd10f18)
if some interference happen logical differential remains same and we still get same result no matter of interference

Resistances on ends of can bus also used for e2e protection
![Resistances](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/b67736cb-67dd-49b4-bfeb-ed5f5cd88918)
It's used for protecting from отражённый сигнал, so voltages wont be repeated on bus

![Gateway](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/6e7edb55-ce77-4881-8873-7a354887e000)
Gateway is used to change msgs from high speed to low speed and vice versa

<h3> Data Link Layer of CAN </h3>

Message frame format:
![Message format](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/14d646a4-7072-4d44-8e1e-5bd5a94c6d74)
Arbitration:
To decide which node will transmit their message on bus one node sends SOF as 0 and everyone start arbitration by - sending their ID on bus
![arbitration1](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/d6f71cfb-616e-44e3-aa7a-04c3e7df061d)
![arbitration2](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/3a150024-8285-4446-abe0-c53cae457201)
DLC - data length code - how much data is there going
RTR - requert to receive data
ID EXT - is there 11 bit id or 29 bit id
There's different type of frames, but you can google them like overloading frame, error frame etc
