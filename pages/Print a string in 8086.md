-
  ```
  ;-----DISPLAY INPUT MESSAGE
  MOV DX, OFFSET INPMSG                
  MOV AH, 09H
  INT 21H
  ```
- Another way with macros
-
  ```
  DISPLAY MACRO MSG
  MOV AH,9
  LEA DX,MSG
  INT 21H
  ENDM
  ```
-