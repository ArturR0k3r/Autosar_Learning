![Pasted image 20230613165514](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/efe0a8a2-367a-4c4f-8c6c-f394fd153b24)
- Basic / Extended tasks
- Preemptive / Non-preemptive
- Context Switch
- Proccessing levels
- Task are placed in Queue with priority so scheduler could find easily oldes task and with highest prio
- Cat1/Cat2 interrupts. 
- Rescheduling в Autosar OS обычно осуществляется в одном из следующих случаев:
	1. Появление задачи с более высоким приоритетом: Если появляется задача с более высоким приоритетом, чем текущая выполняющаяся задача, происходит прерывание текущей задачи и переключение на выполнение новой задачи с более высоким приоритетом.
	2. Завершение задачи: Когда задача завершается или достигает своего временного ограничения, планировщик Autosar OS переключает контекст на следующую задачу с наивысшим приоритетом, готовую к выполнению.
- Relative alarm (timeout) / absolute (at specific hour) alarm. Alarm actions: Task activation, Event setting, Alarm Callback. Os counter can be used for multiple alarms
- Resource Management:
	Management acces to aviable resources (scheduler,CAN,memmory access, etc.)
	It ensures that: two task ain't occuping one resource at the same time, no prio inversion, no deadlocks, access to resource never result in a waiting state
- Scalability Classes 1-4 ; OSEK OS / Schedule Table / Timing Protection / Memory Protection
- Semaphore (variable shared between threads and with two atomic operations: wait/signal) for aviability of resources
![Pasted image 20230614102300](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/81081fdf-ce95-4a7d-8597-4f6c142e497f)
![Pasted image 20230614102319](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/30e7a861-f0b6-4ea3-bbd0-05faa68e9772)
![Pasted image 20230614102328](https://github.com/LivingLegendLL/Autosar_Learning/assets/125698571/0a6319c3-77e7-47e6-bd5f-e6412be0e3a8)
