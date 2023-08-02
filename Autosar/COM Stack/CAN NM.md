- Initiating wakeup and shutdown of CAN bus and synch of all nodes in a cluster
- One CAN cluster can have many nodes. If a node needs to inform other nodes that it needs bus com then it shall transmit periodic Network Management frames
- Three operation modes: Network mode/Prepare Bus-Sleep mode/ Bus-Sleep mode
	Network mode furthere devided in:
	- Repeat Message State
	- Normal Operation State
	- Ready Sleep State
- Waking up of a cluster is done by transmiting network management frame or it receiption serves as awake thing for cluster
- If a node ready to sleep, it stops sending nm frame
![[Pasted image 20230607165157.png]]
- Tow types of wakeup: *Passive* (when other ECU is reason to wakeup and in this case we shoul receive NM frame to keep in this state) ; *Active* (Current ECU is source of wakeup and we sent NM frames)
-  NM frame structure![[Pasted image 20230607165622.png]]
- ![[Pasted image 20230607165645.png]]
- Bus Load Reduction Mechanism for reduction number of frames transmited on CAn so no overload. If Bus load reduction is enabled in a cluster only two nodes having smallest ReducedTime will transmit NM frame. Mechahinsm will activate in Normal Operation state and if LoadReductionEnabled == TRUE
- Partial Networking - to reduce bus load and CPU load. It's reducing some of functionality - different bits requests different node for them to send NM frame..