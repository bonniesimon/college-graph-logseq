title:: OWebSync: Seamless Synchronization of Distributed Web Clients

- Terms/Keywords
	- Groupware : A software that enables users to work collaboratively on projects or files via a network.
	- Synchronization : Process of keeping the data of multiple replicas eventually consistent by means of replication.
	- Vector clocks : Vector Clock is an algorithm that generates partial ordering of events and detects causality violations in a distributed system.
		- Causality : The relationship between cause and effect.
	- Join Semilattice: [[John Mumm - A CRDT Primer: Defanging Order Theory]]
	- Join decomposition (Lossless join decomposition) : It is the decomposition of a relation R into relations R1 and R2 such that if we perform natural join of R1 and R2, we get R.
- Reference Materials
	- [[An introduction to state-based CRDTs]]
	- [[John Mumm - A CRDT Primer: Defanging Order Theory]]
- [[Structure of the OWebSync Seminar]]
- [[Underlying technologies for OWebSync]]
- [Paper explaining LWWRegister](https://hal.inria.fr/file/index/docid/555588/filename/techreport.pdf)
- [Lattice diagram and merging with it](https://blog.acolyer.org/2019/03/11/efficient-synchronisation-of-state-based-crdts/)
# OWebSync
	- Doubts
		- What is a key-value store?
	- OWebSync uses state based CRDTs.
	- It requires less from the message channel unlike operation based approaches.
		- This is since in operation based, if an operation is missed then data will change causing inconsistencies.
		- But in state based, as long as you receive the whole state at some time, you'll be in "eventual consistency"
	- Unlike delta state based, metadata about other clients need not be stored. Here we use Merkle trees to find changes.
	- Merkle trees find the items that need to be synchronized efficiently. This avoids the overhead of full state exchanges between server and client.
	- Working of ORMap in OWebSync
		- We make two extensions to the basic ORMap to make state-based synchronization more efficient.
		- First we extend this data structure with a Merkle tree using the object's logical tree-structure.
			- This means that we keep an extra hash for all items in the observed set.
			- When the child is a LWWRegister, the hash of hash of the value of that register. When the child is another ORMap, the hash of it is the combined hash of the hashes of all its children, lexicographically ordered on the unique tags.
		- Second we do not store a child CRDT inside the observed set, instead we only store the tag, key and hash of that CRDT.
			- Child CRDTs can be store elsewhere.
	- During merge operation, if a key is present in two ORMaps with different tag, the LUB (Lowest Upper Bound) operation will only keep the largest tag and merge the two values according to the rules of the child CRDT.
		- The other tag is considered removed.
		- Here LUB is equal to the Merge operation.