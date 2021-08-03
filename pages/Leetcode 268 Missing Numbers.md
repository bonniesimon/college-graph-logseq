- [Problem statement] (https://leetcode.com/problems/missing-number/)
- Optimal Solution
	-
	  ```c++
	  class Solution {
	  public:
	      int missingNumber(vector<int>& nums) {
	          int result=0;
	          for(int i=0; i<nums.size(); i++){
	              result^=nums[i];
	          }
	          for(int i=0; i<=nums.size(); i++)  result^=i;
	          return result;
	      }
	  };
	  ```
	- This is solved using XOR.
	- Some properties of XOR
		- So what happens is that XOR is associative as well as commutative.
			- So we can re-order the XOR operations in any way and we'll still end up in with the same result.
		- XOR of two similar numbers results in 0.
		- Any number XOR with 0 is 0
	- So if we do 2^3^2^3, effectively what we'll be doing is (2^2) ^ (3^3) = 0 ^ 0 = 0.
		- So if we have a list having numbers that repeats itself even number of times i.e [2, 2, 3, 3] or [2, 2, 2, 2, 3, 3, 3, 3], then if we do XOR of them we'll get 0 as result.
	- The logic of the program is that we initially XOR all the numbers in the given array and store it in results
	- Then we'll XOR the results with all the numbers from 0 to N. There for all numbers except one will repeat it self.
	- So for [3,0,1] input. The operation we will be doing is (3^0^1) ^ (0^1^2^3). So the output of this will be 2 i.e the number that only occurs once. Hence we get the answer.
	- We can use the same logic for the Single Number question.