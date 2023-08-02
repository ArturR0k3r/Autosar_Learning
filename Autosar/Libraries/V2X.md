V2X - Vehicle-To-Everything - Communication between vehicle and any entity that may be affected by vehicle. It's general system that have more specific type of communication:
	V2I (vehicle-to-infrstructure) - traffic lights / lane markers / parking meters
	V2G (vehicle-to-grid) - buildings / loads
	V2N (vehicle-to-network)
	V2C (vehicle-to-clouds)
	V2V (vehicle-to-vehicle) - real-time data exchange with near vehicles
	V2P (Vehicle-to-pedastrian) - wheelchairs / bycecles
	V2D (vehicle-to-device) - Bluetooth / WiFi / Apple CarPlay / Google Android Auto
Main goals - road safety, traffic efficiency, energy savings, mass surveliance.
There are two types of V2X communication dependent on underlying tech: WLAN-based and cellular-based
Within this protocol specification, it is assumed that the data communication between the V2X stack and the V2x Access Layer will happen over Ethernet, but any other communication technology can be used. The V2xRAL does not specify further details for communication over Ethernet such as VLAN, TCP or UDP, Ports, EtherType or other media dependent details.
Security considerations for the communication channel are also not in the scope. It is assumed that any security protocol such as MACsec, IPsec or TLS could be used, since the V2xRAL is located on top of these layers.
Due to the minimum set of data it can be exchanged within a raw Ethernet frame, but can also be placed on top of a protocol such as TCP/IP
The protocol does not require any acknowledgement or segmentation
![[Pasted image 20230616104102.png]]
![[Pasted image 20230616104236.png]]
