- Got the logic from this [video](https://youtu.be/XYQecbcd6_c)
- Solution is
	- Basically take a character and try expanding it and see if it is a palindrome
-
  ```c++
  string s;
  getine(cin ,s); // s = "bonnie";
  string result = s.substr(1, 2); //"on"
  
  // returns a substring substr(pos, pos+count);
  // Second argument is the number of characters after pos that you want to include. Not the end index
  ```
- Source : [substr](https://stackoverflow.com/questions/27992264/c-equivalent-of-python-string-slice)