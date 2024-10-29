# Global Infrastructure
- High availability
- Fault Tolerance

## AWS Regions
- are geographically isolated areas
- They Ensure Regional data sovereignty
- They contain three or more **Availability Zones** (data centers)
- Choosing a region
	- **Compliance** requirement (data must live in Canada)
	- **Proximity** to consumers (lower latency)
	- **Feature Availability** (not all regions have all AWS features)
	- **Pricing**: some locations are more expensive

## Availability Zones
- One region consists of multiple data centers, therefore multiple availability zones
- AWS recommends running across at least two availability zones in a region
- ELB runs across all availability zones
- us-east-1a, us-east-1b are two different zones within one region, us-east-1

## AWS Edge locations
- Run AWS Cloudfront (CDN)
- Run AWS Route 53 (DNS)

## AWS Outpost 
- Data Center Isolated in your building
  
## Provisioning

- All provisioning is done through API Calls
- API Calls come from either
	- The **AWS Management Console** (Web Interface) for Manual Provisioning
		- Useful mainly for Bills, Test environments, Monitoring
	- **AWS CLI** - Command Line Interface
	- **AWS SDK** - Software Development Kit
	- **AWS Elastic Beanstalk**
		- Give it your application code and desired configurations
		- Makes your AWS environment for you
		- Helps you focus on your business application, not the infrastructure
	- **AWS CloudFormation**
		- IaC Infrastructure as Code
		- Specify the desired end state in a yaml/json config file