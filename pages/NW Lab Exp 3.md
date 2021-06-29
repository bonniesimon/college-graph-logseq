- Readers writers problem relates to an object that is shared between multiple process.
- Such an object is also called *critical section*.
- Some of these processes are readers, they only want to read data from the object.
- some are writers, they want to write into the object.
- Readers writers problem is used to manage synchronization so that there is no problems with the object data.
- If two readers access the data at the same time, there is no problem.
- However if two writers or a reader and a writer access the data at the same time, there are problems.
- To solve such an issue, writers must be given exclusive access to the object.
	- When a writer is accessing the object, no other reader or writer can access the same object at the same time.
- Such solution can be implemented using Semaphores.
- Reader process
	-
	  ```
	  wait (mutex);
	  rc ++;
	  if (rc == 1)
	  wait (wrt);
	  signal(mutex);
	  .
	  . READ THE OBJECT
	  .
	  wait(mutex);
	  rc --;
	  if (rc == 0)
	  signal (wrt);
	  signal(mutex);
	  ```
	- `mutex` and `wrt` are semaphore initialized to 1.
	- rc is a variable initialized to 0. It denotes the number of readers accessing the object.
	- `mutext` ensures mutual exclusion, `wrt` handles the writing mechanism and is common to the reader and writer process code.
	- When `rc` becomes 1, wait operation is used on `wrt`, so the writer can't access the object anymore.
	- After the operation is done, `rc` is decremented.
	- When it becomes 0, signal operation is used on `wrt`. So writer can access the object now.
- Writer Process
	-
	  ```
	  wait(wrt);
	  .
	  . WRITE INTO THE OBJECT
	  .
	  signal(wrt);
	  ```
	- When writer wants to access the object, wait on `wrt` is done. Thus no other writer can access the object anymore.
	- When writer is done writing into the object, signal operation is performed on `wrt`.
# References
	- https://www.tutorialspoint.com/readers-writers-problem
	- https://www.geeksforgeeks.org/readers-writers-problem-set-1-introduction-and-readers-preference-solution/