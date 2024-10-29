# EC2 - Elastic Cloud Computing
- You do not pay for stopped or terminated instances
- **Hypervisor** is responsible for multi-tenancy and isolation of virtual machines
- Choose OS: Windows or Linux
- **Vertical Scaling:** Make instances bigger or smaller when needed

## EC2 Instance Families
There are different Instance Types grouped under an instance family

- **General Purpose Family**
	- Balanced resources
	- Diverse workload
- **Compute Optimized Family**
	- Gaming servers
	- HPC High-Performance Computing
	- Batch processing workload
	- Scientific modelling
- **Memory Optimized Family**
	- Memory Intensive Tasks
	- High-performance database
- **Accelerated Computing Family**
	- Floating Point Calculations
	- Graphics processing
	- Data Pattern Matching
	- Utilize hardware accelerators
- **Storage Optimized Family**
	- High performance for locally stored data

## EC2 purchase options

- **On-Demand**
- **Savings Plans**
	- 1 or 3 years commitment on hourly spend to an instance family and Region
	- There is no commitment to instance type, size or quantity
- **Reserved Instances**
	- 1 or 3 years plan
	- Full, partial or no upfront payment
	- **Standard Reserved Instances**
		- Specific to an instance type, size, OS and tenancy (default or dedicated)
		- Optionally specify the zone for capacity reservation
	- **Convertible Reserved Instances**
		- Different instance types and multiple zones are available
- **Spot Instances**
	- On-the-spot interruptible machines
	- Ideal for background processing jobs
	- interruptions could happen
- **Dedicated Hosts**
	- physical server dedicated to your use
	- most expensive option

## EC2 Scaling
- **Auto-scaling Group**
	- Minimum Instances
	- Desired Instances (optional, defaults to minimum)
	- Maximum Instances
- **ELB** **Elastic Load Balancing**
	- Decoupled Architecture
	- Handles Front-End Traffic and Back-End Requests
	- High performance
	- Cost Efficient
	- Highly available
	- Automatically scalable
