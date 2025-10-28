# ansibleebsautomation

This repo guides in deploying a solution on Ansible using Dynamic Inventory the collects information of all the public IP EC2 instances across all the regions. Modifying `ansible_host: public_ip_address` to `ansible_host: public_ip_address` will enable host to ssh EC2 instance using private IP however, it will only work if the instances are accessible using private IP. 
The solution uses Ansible Vault to securly store IAM credentails and detects the low disk utilization and send alerts using Amazon SNS. 

## Key highlights of the solution
1. Utilizing existing configuration management tool - Ansible.
2. Securely stores IAM credentials and uses fine-grained access control to provide the least required access.
3. Utilize AWS APIs.
4. Gathers Amazon EBS volume data from all the Amazon EC2 instances.
5. Scalable solution as it can manage resources across regions and AWS accounts.
6. Proactively increase the volume size by 10% if no action is taken 1 hour after the alert.
