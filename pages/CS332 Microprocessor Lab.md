- [Repo having ASM programs in the format we did it MIT](https://github.com/mitcse/CSE-Labs/tree/master/MP%20Lab)
- [repo has programs in our format, check out reverse string program](https://github.com/apsrcreatix/8086/blob/master/REVERSE_OF_STRING.asm)
- [Repo with ASM programs](https://github.com/jacobjohn2016/8086-Programs)
- [Repo Having Code for matrix addition](https://github.com/kingspp/8086-MicroProcessor)
- [Repo having code for decimal to hex](https://github.com/rajmehta18/8086programming)
- [some ASM programs](https://www.scribd.com/doc/61792959/8086-lab-programs)
- [[Print a string in 8086]]
- [[Print a number under 10 in 8086]]
- [[Exp 11 : Check for substring in a string]]
- [Inputing and outputing hexadecimal](https://getassemblycode.blogspot.com/2017/08/assembly-hexadecimal-input-output-add.html)
- Exp 12
	- [what hex values mean](http://www.nha.dk/hex.html)
- [[MP Lab Exp 15]]
- Correct Programs
	- 12 - EXP12
	- 13 - HEXTOBCD
- Reading String macro and printing string macro
-
  ```assembly
  PRINTS MACRO P
  MOV DX, OFFSET P
  MOV AH,09H
  INT 21H
  ENDM
  
  
  READS MACRO S
  MOV DX, OFFSET S
  MOV AH,3FH
  INT 21H
  ENDM
  
  DATA SEGMENT
  	NUMS DB 5 DUP(?)
  DATA ENDS
  
  CODE SEGMENT
      READS NUMS
      LEA SI, NUMS
     
     
      ; using SI like
      
      MOV AL, [SI]
      INC SI
  CODE ENDS
  ```
-
  ```assembly
  LEA DI, NUM 
  ```
- Above code means that DI point to NUM.
-
  ```assembly
  ;reading from keyboard into ascii form
  MOV AH, 01
  INT 21H
  
  ;writing to screen in ascii form
  MOV AH, 01
  INT 21H
  ```
- For above, value will be in AL register
-
  ```
  ;setting BX to 0
  XOR BX, BX
  ```
-