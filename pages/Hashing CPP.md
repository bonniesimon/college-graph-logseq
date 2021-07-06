- Hash maps is a data structures that allows the following operations in an efficient manner.
	- insert(key, value)
	- search(key)
	- delete(key)
- Values can be pairs.
- C++ has two types of hash maps :
	- unordered_map
		- uses separate chaining with hash function
		- If the items are in unsorted then use this
		- O(1) for insertion, deletion and searching.
		- But time taken if rehashing is required.
	- map
		- uses balanced BST / Red Black tree
		- If items are to be sorted then use this
		- O(log N) for insertion, deletion and searching
-
  ```c++
  unordered_map<string, int> m;
  
  // First way to insert
  m["mango"] = 100;
  
  // Second way to insert
  m.insert(make_pair("Apple", 120));
  
  // Search
  if(m.count("Apple") == 1){
      // print cont
  }
  
  // Also use iterators to search
  auto f = m.find("mango");
  if(f != m.end()){
      cout << (f->second);
  }
  
  // Deletion
  m.erase("mango");
  ```
	- `m.count(key)` return 1 if key exists in hash map else returns 0
	- if f points to `m.end()`, then key not found.
	- To use `map`, just replace `unordered_map` with `map` and it'll work just fine.