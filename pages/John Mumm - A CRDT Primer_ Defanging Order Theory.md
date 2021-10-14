title:: John Mumm - A CRDT Primer: Defanging Order Theory

- [video-link](https://youtu.be/OOlnp2bZVRs)
- [resources of the talk](https://github.com/jtfmumm/curryon2018)
- Why CvRDTs are good
	- You can merge them in any order
	- You can merge the same one multiple times
	- You can use them even if messages are delayed, reordered, or duplicated.
	- They always converge to a global vaule.
	- They have these properties because they form a join semi-lattice.
	- So instead of calculating the total number of likes in all servers, we can pass only little information and converge on to the global value.
- Explains a lot about the DCS part of CRDT. Explains what a monotonic join semi lattice is. And what a join semi lattice is.