<h1>What is E2E in general and as library</h1>
SW mechanismы to ensure data integrity in case of occuring error in data transmission.

## The common communication errors

1) **Data Loss** 
2) **Repetition** - same data information is received in successive messages
3) **Timeout** - can only occure in systems with defined timing requirements (which means sender and receiver has common understanding of "time")
4) **Incorrect Sequence** - happens in highly distributed systems. Data arrives at receiver in another sequence than originally sent. (ex. firstly comes CF and not the FF). This can happen in case of buffered communication
5) **Insertion of an unintended message** - additional msg or part of it is added in stream. Occurs very unlikely and protected via hardware perspective
6) **Data Corruption**
7) **Addressing Error** - Data sent to wrong destination and treated as correct data. Usually protected by a unique ID to data or to sender/receiver
8) **Constant "over-" Transmission** - different or the same message are transmitted over and over again, leading to a bus overload and detaining other safety-relevant data.
9) **Masquerading Error** - unique DataID exist, but data disgues itself and accepted although it just pretends to be the one correct. Can happen in case of corruption of DataID.


## The communication error detection mechanisms

- **Hardware Redundancy**
- **Time Redundancy** - same information is transmitted twice via two different messages in different time slots
- **Checksum** - Just algorithm itself // Дата просто дошла тому кому нужно
- **Sequence Counter**
- **Message-ID**
- **CRC** - Whole data block is used as base for calculation for generator to create a memory-dependent signature that is recalculated at receiver side. // Дата дошла не просто только тому кому нужно, но и ещё всё что в дате должно быть таким же как я и отправил
- **Parity bit**
- **EDC(Error Detection Codes) / ECC(Error Correction Codes)** - There exist several different algorithms for such codes that can be described by their Hamming Distance. The Hamming Distance describes how many bit failures of the code can be detected. A Hamming code with distance d can correct d-1 errors.
- **Timestamps**
- **Cryptographic techniques**
- **Information Redundancy** - same info twice in one msg
- **Identification procedure** - ex. seed-key
- **Retry mechanisms**
- **ACK**


Safety-mechanisms in E2E had to meet ASIL-C requirements considering ISO-26262 standart.

E2E library is where the algorithms for E2E protection are implemented. It provides mechanisms up to ASIL-D level. Profiles as well as state machine of E2E are configurable.

!!! E2E helps in detection of errors, but not their handling !!!

#### Steps to use E2E Library
1) Select architectual approach to use E2E library
2) Select data elements to be protected and with wich E2E profile
3) Determine settings for each data element or signal roup to be protected
4) Developing necessary code for invocation of E2E library functions
