- Doubts
	- Why are we doing `PRINTS S` in the Macro
	- why using `SI + 2` in macro
- Algorithm of `OUTD` proc
	-
	  ```
	  push bx to stack
	  push cx to stack
	  push dx to stack
	  bx = 10h
	  dx = 0000h
	  ch = 00h
	  ax / bx ; dx has remainder ; dx has last digit
	  push dx to stack
	  ch ++
	  if all digits pushed to stack goto 11 else go to 5
	  pop stack to dx
	  if dx > 10, goto 13; else go to 15
	  	add 37h to convert it to ascii
	  	print it
	      goto 20
	  else 
	      add 30h to dx to covert number 0-9 to ascii
	      print it	
	      goto 20
	  ch--
	  if ch!=0 goto 11
	  pop stack to dx
	  pop stack to cx
	  pop stackt to bx
	  ```
	-