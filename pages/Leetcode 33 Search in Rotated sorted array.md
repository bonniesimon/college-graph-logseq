- Problem [Url](https://leetcode.com/problems/search-in-rotated-sorted-array/)
- Solution
  collapsed:: true
	- Take low mid and high.
	- Check if element in mid? if yes return
	- Else, then check if whether low - mid or mid - high is sorted. Only one will be sorted.
	- If low to mid, check if low <= target <= mid. If yes => return
	- else if high to mid, check if mid <= target <= high
	- If not inbetween the sorted part, then place low, mid and high in the unsorted part and do the same checks as above.