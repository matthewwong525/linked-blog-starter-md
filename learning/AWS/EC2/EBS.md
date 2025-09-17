1. An EBS Volume stands for ***Elastic Block Store***. It's a network drive that you can attach to your instances while they run. 
2. EBS Volumes allow us to persist data, even after the instance is terminated.
3. Can only be mounted to one instance at a time.
4. They are bound to **a specific availability zones** similar to *network USB stick*.
	  - Can [[Snapshot]] from one AZ to another AZ
5. EBS Volume is a network drive and not a physical drive.
	  - It uses n/w to communicate to the drive, so there might be a bit of latency.
	  - It can be detached from one EC2 instance and attached to another very quickly. 
6. EBS - Delete on termination flag
	1. Control EBS behavior when associated EC2 instance terminates.
	2. By default, root EBS associated with EC2 instance has delete on termination flag set to true, other EBS instances are set to false.
7. https://aws.amazon.com/blogs/aws/new-elastic-network-interfaces-in-the-virtual-private-cloud/ 
8. 