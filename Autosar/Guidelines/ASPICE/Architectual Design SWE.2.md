Goal - how the functionality is going to be implemented

SW requirments: WHAT
SW architecture: HOW

Aspects in documentations of SW architecture:
	1) Define the adequate architectual view - often architectuare is in physical view (block diagram) but it's not enough. Additional views can be: Dynamic views / Specific functional views / State-flow diagrams / Interfaces. **UML** / **SysML** tool should be used for consistancy check
	2) Document interfaces accurately - expected contents:
		- Names
		- Types
		- Units
		- Resolutions
		- Ranges
		- Default values
		Without this info, proper [[Integration Tests SWE.5]] isn't possible. Also use UML/SysML tool (ex. PREEvision of Vector)
	3) Traceability: SW architectuare - SW requirements
		Purpose:
			a) Consistancy
			b) Impact assessment
			c) Reporting of stakeholder expectations (identify coverage reports)