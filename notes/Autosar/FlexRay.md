On physic level:
	Unshielded twisted pair cables.
	Supports dual-channel configurations <- more redundancy
	Also resistances
	Wires is possible to be electrical / optical
	Time based (TDMA - time-Division Multiple Access) - Time slots for each node to communicate. Each node allowed to communicate only when their node is active
	![Pasted image 20230616141405](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/92ad3912-6299-4019-98e0-bf8658941e2e)
	![Pasted image 20230616141457](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/91fed23c-bb0d-4c7e-b516-dced10b10929)
	Multi-drop passive connection - one network cable that connects each ecu in a network.
	Active Star Connection - ![Pasted image 20230616141706](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/2d6a44a3-1be2-468b-8190-538ea5fdee27)
On protocol level:
	254 Bytes payload
	![Pasted image 20230616145634](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/03f2b17b-352e-4442-a75a-4ac99747ab2b)
	Two bus levels Data_1 and Data_0 are dominant bus levels
	![Pasted image 20230616150023](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/543d834b-22d2-4de1-b1e6-cb888a6739a9)
	BP - Bus Plus ; BM - Bus Minus
	Starts with indicator bits and ends with CRC bits
	![Pasted image 20230616150242](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/8dba5ca3-ab3c-4083-8c44-25c1ba97b77d)
	1. Static Segment (Статический сегмент): Статический сегмент в протоколе FlexRay представляет собой часть временного цикла, где заданы временные слоты с фиксированной продолжительностью. В статическом сегменте устанавливаются временные слоты для отправки сообщений с высокими временными ограничениями и высоким приоритетом. Этот сегмент обеспечивает жесткое распределение времени и предназначен для критически важных сообщений.
    2. Dynamic Segment (Динамический сегмент): Динамический сегмент в протоколе FlexRay используется для передачи сообщений с более низким приоритетом и менее жесткими временными ограничениями. В отличие от статического сегмента, продолжительность динамического сегмента может изменяться в зависимости от требований приложения. Он предоставляет гибкость для передачи менее критически важных данных и может использоваться для адаптации к изменениям в трафике.
    3. Symbol Window (Окно символов): Окно символов - это временное окно в протоколе FlexRay, которое определяет длительность одного цикла передачи данных. Оно состоит из статического сегмента, динамического сегмента и промежуточных символов. Внутри окна символов определяются и управляются временные слоты для различных типов сообщений и задач.
    4. Network Idle Time (Простой сети): Простой сети (Network Idle Time) - это период времени в протоколе FlexRay, когда сеть находится в неактивном состоянии и нет передачи данных. В этот момент сеть свободна и не занята передачей сообщений. Простой сети может использоваться для различных целей, таких как обновление конфигурации сети, обнаружение новых узлов или выполнение диагностики.
    Two CRC in frame: 11 bit header / 24 bit trailer
    Bus Guardian - Only allows fr tranceiver to place data received from fr controller on the bus, if it conforms to the communication schedule. Although no protection in dynamic segment
