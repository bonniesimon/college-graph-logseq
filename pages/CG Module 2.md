- Syllabus
	- Line Drawing Algorithm- DDA, Bresenham’s algorithm –
	- Circle Generation Algorithms –Mid point circle algorithm, Bresenham’s algorithm-
	- Scan Conversion-frame buffers – solid area scan conversion –
	- polygon filling algorithms
- ![Module 2 by Miss.pdf](../assets/Module_2_by_Miss_1637040594953_0.pdf)
- Graphics Output Primitives
	- Points
		- A point is shown by a illuminating pixel on screen
	- Lines
		- A line segment is defined in terms of its two endpoints
	- Line is produced by means of illuminating a set of intermediary pixels between the two endpoints
# Line Drawing Algorithms
	- Line drawing is done by calculating the intermediate positions along the line path between the specified end point positions
	- ## DDA
		- Advantages
			- It eliminates multiplication
			- Does not calculate coordinates based on the complete equation (uses offset method)
		- Disadvantages
			- Round offs are accumulated, thus line diverges more and more from straight line
			- Round off operations take time
	- ## DAA vs Bresenham's
		- |                       | DAA                                                              | Bresenham's                                    |
		  |-----------------------|------------------------------------------------------------------|------------------------------------------------|
		  | Arithmetic            | uses floating points i.e. real arithmetic                        | Uses fixed points i.e. integer arithmetics     |
		  | Operations            | uses multiplication and division                                 | uses subtraction and addition                  |
		  | Speed                 | relatively slow due to real arithmetic                           | Faster due to integer arithmetic               |
		  | Accuracy & Efficiency | relatively less accurate and efficient                           | More efficient and accurate                    |
		  | Round off             | round off coordinates to the integer that is nearest to the line | Does not round off but takes incremental value |
		  | Expensive             | More expensive due to real arithmetic                            | Less expensive due to integer arithmetic       |