# A highly-available & scalable Infrastructure with automated maintenance

<br>
The infrastructure, as shown in the diagram below, utilises several AWS components to provide highly 
reliable access to an Aurora RDS database. The system was designed with scaleability and maintainability 
in mind to ensure continuous availability of the deployed resources, while running as cost efficient as 
possible. All code has been written in Terraform.

<br>
The following is a brief summary of the main components that have been used to build this system and
their functionality therein:
<br>
<br>

### Auto-scaling and load balancing

To ensure high availability while keeping cost low, the auto-scaling group was configured to launch or stop
instances according to the given CPU utilisation.The launch template makes use of a Docker image to 
provide a stable launch process with minimal time between launch and being serviceable.. Load balancing 
ensures that incoming traffic is distributed evenly across all active instances. 
<br>
<br>

### Host-monitoring in conjunction with a Lambda function for automated maintenance
In order to further increase availability, while reducing maintenance effort, CloudWatch has been configured
to monitor instance health in regular short intervals. If any instance should fail the health check, a Lambda
function is triggered that initiates an instance shut-down. Additionally, SNS notifies any subscribers to the 
occurrence of a failed health check. 
<br>
<br>

### Logging and system accessibility
All system metrics are logged via CloudWatch and CloudTrail and forwarded into an S3 bucket. A separate
bastion host is provided to enable manual access to the infrastructure if need be. 


![capstoneDiagramm](https://github.com/Jan0770/capstoneProject/assets/101402107/58194299-5ed7-44ab-892a-3e5c5bd7bfbf)
