# Networking  
## Amazon VPC - Virtual Private Cloud
- Create Subnets
	- Private Subnets
		- To Isolate databases
	- Public Subnets
		- Customer-facing websites or APIs
		- Put EC2 instances and ELB (Elastic Load Balancer)

### VPC Components:

#### Internet Gateway
- Allows Public Traffic from the Internet to access your VPC

#### Virtual Private Gateway
- Allows Traffic From VPN connections

#### AWS Direct Connect
- Dedicated physical private connection between your data center and a VPC
 
#### Network Hardening
- **Network ACL** - Access Control List
	- Verifies that inbound and outbound traffic is on the allowed list on the subnet
	- Stateless
	- Defaults to allow all inbound and outbound traffic
	- Each AWS Account includes a default ACL
- **Security Groups**
	- All EC2 instances are created in a security group
	- You can use a security group for multiple EC2 instances
	- Defaults to deny all inbound and allow all outbound traffic
	- Security Groups filter inbound traffic by port (i.e., Allow 443 HTTPS for a web server)
	- Stateful
		- Remembers a packet request and will automatically let the response back in, regardless of inbound security group rules

## Amazon Route 53 DNS
- Latency-based routing
- Geolocation DNS
- Geoproximity routing
- Weighted round-robin
- Register Domain Names

## Amazon Cloud Front
- CDN