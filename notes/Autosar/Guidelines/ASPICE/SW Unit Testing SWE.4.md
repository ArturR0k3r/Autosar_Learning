If Unit Testing isn't done, there will be two consequences:
	1) Not all problems are guaranteed to be found later
	2) Risk of repeating previous tests

Three aspects in unit verificattion process:
	1) Define a strategy in unit verification. Strategy - easy to understand instructional description. Main purpose of strategy - Description of how you inted to demostrate that SW units are compliant with SW detailed design. Three types of verifications are required:
		- Static and dynamic analysis (check code with analysis tools)
		- Code reviews
		- Unit tests
	In addition ASPICE requires a regression test strategy. Refer to [[Integration Tests SWE.5]].
	2) Bidirectional tracebility and consistency. Types of traceability:
		- Know the corresponding test specification
		- Know the results of code reviews and static analysis
		- Know the unit test results
	Consistency - unit is linked to the correct test and not to the other unit. Test covers unit completly. If what additional tests must be linked. No faulty tests.
	3) Summirize and communicate test result. Test summary report. Same as in [[Integration Tests SWE.5]]
	Report also not showing compliance with the [[SW Design + Unit Construction SWE.3]]