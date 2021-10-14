- Synchronization frameworks are
	- Operational Based
	- State Based
	- Delta-state based
- Operational Based
	- Google docs uses operational based.
	- Works by using a central server to transform the operations for other clients to deal with concurrent changes.
	- However it is not resilient against message loss or out of order messages.
- State Based
	- Uses State Based Convergent Replicated Data Types
	- Resilient against message loss.
	- This method is used in Riak.
		- Riak, in their website states that "As long as your Riak KV client can reach one Riak server, it should be able to write data.".
		- So you connect to one server and be able to modify your data. But the change has to be notified to all the other servers. This background synchronization between data centres is done using State Based method.
- Delta-state Based
	- Need less of the message channel than the operational based approaches.
	- Use vector clocks to calculate delta updates.
	- It does not work well with the uncertainty of web where it is often unclear whether a client will ever connect to a server again.
- OWebSync
	- a generic web middleware for data synchronization in browser based applications and interactive groupware.
	- It supports offline usage with fast resynchronization as well as continuous and interactive synchronization between online clients.
	- It provides a generic, reusable data type, based on JSON, that web application developers can leverage to model their application data.
	- One can nest several map structures into each other to build a complex tree structured data model.
	- These data types support fine grained and conflict-free synchronization by leveraging state based Conflict-free Replicated Data Types(CRDTs).
	- OWebSync solves the scalability issue that comes with operation-based approaches.
	- It reduces required bandwidth by combining several tactics such as Merkle-tress embedded in the tree structured data, virtual Merkle tree levels and message batching.
- Operational Transformation
	- It is a technique used to synchronize concurrent edits on a shared document.
	- It works by sending the operations to the other replicas (clients).
	- The operations are not necessarily commutative, which means that they cannot be applied immediately on other replicas
		- Commutative means that the order is not important.
	- A concurrent edit might conflict with another edit.
	- Therefore a central server is used to transform the operations for the different replicas, so that the resulting operations maintains the original semantics.
	- Messages can get lost or can arrive in the wrong order.
	- Hence OT is not resilient against message loss and long-lasting offline situations.
	- [image](https://hackernoon.com/operational-transformation-the-real-time-collaborative-editing-algorithm-bf8756683f66) taken for the seminar PPT.
- Conflict-Free Replicated Data Types (CRDT)
	- [CRDTs for Non Academics](https://youtu.be/vBU70EjwGfw)
		- A good video that explains CRDTs.
	- CRDTs are data structures designed for replication that guarantee eventual consistency without explicit coordination with other replicas.
	- Conflict-free means that conflicts are resolved automatically in a systematic and deterministic way, so no manual conflict resolution is required.
	- Two types of CRDTs are CmRDTs and CvRDTs.
	- Commutative Replicated Data Types(CmRDTs)
		- uses operations to obtain consistency just like OT.
		- concurrent operations in CmRDTs must be commutative and can be applied in any order.
		- Therefore no central server is required to make transformation on the operations.
		- Similar to OTs, CmRDTs require a reliable message broadcast channel.
		- Casual ordering is required in some cases.
	- Convergent Replicated Data Types (CvRDTs)
		- CvRDTs are based on the state of the data type.
		- Updates are propagated between replicas by sending them the whole state and merging the two CvRDTs.
		- CvRDTs require little from the message channel. Messages can be lost or be out of order without a problem since the whole state is sent.
		- However this state can get very large and needs to be communicated every time.
- Delta-state CvRDTs
	- Variant of state based
	- Only a part of the state (delta) that changed needs to be communicated for synchronization.
	- When a client does an update, a new delta is generated that reflects the update done by the client to the other clients.
	- Each client keeps a list of the deltas and remembers which clients have already acknowledged a delta.
	- As soon as all clients acknowledge a delta, that delta is discarded because is update is reflected in the state of all the clients.
	- If a client was offline and missed too many deltas, then the whole state should be passed.
	- Delta CvRDTs have some issues with web applications. It is often unclear whether a client will come back online or not in the future.
	- Keeping extra metadata for all those clients that require certain deltas can result in a large storage or memory overhead. Sending the full state on the other hand  is also not efficient when the state is large.
- LWWRegister
	- A Last Write Wins Register is a CvRDT that contains exactly one value (string , number or boolean) and a time stamp of the last change.
	- This time stamp will be used to merge another replica of this LWWRegister.
	- Value associated with the highest time stamp is kept.
- ORMap
	- It is a map data type that can be modified concurrently and will eventually react the same state everywhere.
	- It is "eventually consistent"
	- Working of ORMap from [github/observed-removed-map](https://github.com/t-mullen/observed-remove-map/blob/master/README.md)
		-
		  ```
		  var map1 = new OrMap('bob')
		  var map2 = new OrMap('alice')
		  
		  // let's provide a "delay" function to simulate concurrency on a network
		  function delay (cb) {
		    setTimeout(cb, 3000) // 3 seconds of delay!
		  }
		  
		  // let's "connect" our two maps
		  map1.on('op', op => delay(() => map2.receive(op)))
		  map2.on('op', op => delay(() => map1.receive(op)))
		  
		  // both Bob and Alice simulatenously set "a" to different values
		  map1.set('a', 0) // {a:0}
		  map2.set('a', 1) // {a:1}
		  ```
		- Concurrent edits to different keys can be made without a problem
		- Edits to the same key (here 'a') and tag will be delegated to the child CRDT (could be the value which is also a CRDT: either another ORMap or LWWRegister)
- Merkle Trees
	- Merkle trees or Hash tress are used to quickly compare two large data structures
	- A hash tree or Merkle tree is a tree structure in which each leaf node is a hash of a block of data and each non-leaf node is a hash of its children. [source](https://youtu.be/s0fruNfgW30)
	- In Merkle trees, each node contains a hash.
	- The values of the leaf nodes are hashed.
	- Intermediate nodes contains hash of hashes of its immediate children.
	- Thus if the top level hashes of two data structures match, then the data structures are identical.
	- Otherwise the tree can be descended using the mismatching hashes and the mismatching items can be identified.
	- Sub-trees that have equal hashes will always be identical so their children need not be verified.
	- Git uses Merkle tress to identify changes.
	- In OWebSync, Merkle-trees are used internally to quickly find data changes.