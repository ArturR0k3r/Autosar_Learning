Purpose - Check SW [[Architectual Design SWE.2]]. This include:
- Checking Interfaces
- Checking Dynamic behaivour
- Checking Resource consumption

It helps for obtaining more robust sw at lower cost.

Important points for integration tests:
1) Define a strategy for integration and integration testing
	- Strategy - easy to understand instructional description
	- Integration test strategy - describes a SW team's workflow
		- Individual contributor's test
		- Continuous integration
		- Final integration tests
	- Regression test strategy - if in SW something is changed, everything that hasn't changed works fine

2) Bidirectional traceability and consistency
	- Tracebility - for each relevant architectual element you can localize corresponding test
	- Consistancy - Linking the subject to the correct test, covering subject completly

3) Summarize and communicate the test results
	- Test summary report - demonstrating compliance with architecture. (report ex.: overall 500 test to be performed; 49 failed; 55 can not be performed). Nothing about why test failed and what the risks are.