- Solved without referring solution
- Need to see if improved solution exists
	- The solution I found
	  collapsed:: true
		- is to sort the two string and compare them.
		- If they are equal after sorting then they are anagrams
	- Optimized solution
	  collapsed:: true
		- Use a map.
		- map contains <char, int> i.e character and it's count
		- When we encounter a character in s, we increment the count of that character in the map
		- When we encounter a character in t, we decrement the count of that character in the map
		- In the end we check if the value of any char in map is greater than 0. If any is greater than 0 then return false.