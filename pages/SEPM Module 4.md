# Syllabus
	- Coding – programming practice, verification, size measures, complexity analysis, coding standards. Testing – fundamentals, white box testing, control structure testing, black box testing, basis path testing, code walk-throughs and inspection, testing strategies-Issues, Unit testing, integration testing, Validation testing, System testing
# Coding
	- Coding is done after the design phase is completed and design documents are reviewed successfully.
	- Inputs to coding phase is the design document
	- Design document contains
		- High level design in the form of structure chart
		- Detailed design in the form of module specification(MSPEC)
	- ## Coding Standards and Guidelines
		- Any organization would require their programmers to adhere to certain well defined and standard style of coding called coding standards.
		- Why coding standards is required
		  collapsed:: false
			- A coding standard gives a uniform appearance to the codes written, regardless of who wrote it.
			- It enhances code understanding
			- It encourage good programming practices.
		- Coding standard defines certain rules like
		  collapsed:: false
			- the way variables are named,
			- the way code is laid out,
			- error return convections, etc.
		- Some Coding standards
			- *Rules for limiting the use of global*
				- These rules list what types of data can be declared global and what local and what not.
			- *Contents of the headers preceding codes of different modules*
				- Information contained in the headers in different modules
			- *Naming convections for local, global and constant identifiers*
			- *Error return convections and exception handling mechanisms*
			- *Do not use a coding style that is too clever or too difficult to understand*
			- *Avoid obscure side effects*
			- *Do not use an identifier for multiple purposes*
			- *Code should be well documented*
			- *The length of a function should not exceed 10 lines*
			- *Do not use goto statements*
	- ## Code Review
		- Code review for a module is done after the module is compiled successfully and all syntax errors are fixed.
		- They are cost effective way to reduce coding errors and to produce high quality code.
		- Two types
			- Code Walkthrough
				- Informal code analysis technique
				- A module is taken for review after coding and compiling it successfully.
				- Few members of the dev team are given the code to walkthrough.
				- Objective : Discover Algorithmic and logical errors in the code.
				- Each member takes a test case and manually traces the execution of the code.
				- Discuss the finding from the walkthrough with the coder who wrote the code.
			- Code Inspection
				- In contrast to code walkthrough, the aim of code inspection to detect some common types of error due to oversight and improper programming.
				- Adherence to coding standards are also checked.
				- Most frequently occurring errors are noted. These are used during code inspection to check if the code being tested are free off such errors.
				- Frequent errors include
					- Array out of bounds
					- Use of uninitialized variables
					- Infinite loops
	- ## Size Measure
		- The estimation of size is very critical and difficult area of project planning. It indicates the size of the project.
		- Two methods
			- Lines of Code
			- Function Point
# Testing
	- Testing = Verification + Validation
	- Verification (Are the algorithms coded correctly)
	  collapsed:: false
		- Ensuring that the software correctly implements the intended function or algorithm.
	- Validation (Does this meet the client requirements)
	  collapsed:: false
		- Ensuring that the software has been build according to the customer requirements.
	- A successful test is a test that makes the system perform incorrectly and so exposes a defect in the system.
	-
	  #+BEGIN_QUOTE
	  "Test show the presence not absence of defects" - Dijkstra
	  #+END_QUOTE
	- Software testing has two main goals
		- To demonstrate that the software meets it requirements
			- This leads to validation testing.
			- In validation testing, you expect the system to perform correctly using a given set of test cases that reflect the systems actual behaviour.
			- A successful test is one where the system performs correctly
		- To discover faults and defects in the software.
			- This leads to defect testing.
			- Here test cases are designed to expose defects in the software.
			- A successful test is one that exposes a defect that causes the system to perform incorrectly.
	- The testing process includes
		- Component Testing
			- Testing individual program components
			- Done by the developers, is based on the intuitive understand of how the components should operate.
		- System Testing
			- Testing groups of components integrated to create a system or subsystem.
			- Based on a written system specification, done by a separate team.
	- ## Testing Policies
		- Testing policies are a subset of the all the possible test cases that the software companies chooses to be tested.
	- ## Unit Testing
		- Concentrates on each component/function of the software as implemented in the source code
		- Two Strategies
			- ### White Box Testing
			  collapsed:: false
				- All statements and conditions are executed at least once
				- Two Types
					- **Basis Path Testing**
						- It is a white box testing technique based on the control structure of a program.
						- Using this structure a control flow graph is prepared, various paths on the graph are executed as a part of testing.
						- Since this testing is based on the control structure of the program, it requires complete knowledge of the program's structure.
					- **Control Structure Testing**
						- Consists of three types of testing
							- Condition testing
								- Ensures that logical conditions and decision statements are free from errors.
							- Data flow testing
							- Loop testing
			- ### Black Box Testing