- Segmentation of messages which have a payload of more then 8 bytes
- PDUR table
- Staying in services layer and providing segmentation for [[PDUR]] and [[Can Interface]]
- Reasembling segmented messages
- Different channel modes (half/full duplex)
- Physycal or Functional communication types
- Frames:
	**FF** - First Frame - 4 bits frame type (0x1) ; 12 bits data payload size ; 3rd byte SID resp ; 4/5 byte DID ; remaining is initial part of data payload
	
	**FC** - Flow Control - 4 bits frame type (0x3) ; 4 bits Flow Status (0 - Clear to Send/ 1 wait for next FC/ Abort communication) ; 1 byte Block Size (0 - Send all CF / N - send N CF) ; 1 byte STmin (Minimum time gap between CF 0x00 -> 0x7f num of ms / 0xF1 - 0xF9 gap in 100 ms)
	
	**CF** - Consecutive Frame - 4 bits frame type (0x2) ; 4 bits index counter that increments ; 7 bytes for payload
- Addresing formats (ext/standart)
- Padding pattern
- Sync/Asynch transmission