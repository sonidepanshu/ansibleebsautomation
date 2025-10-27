# ansibleebsautomation

This repo guides in deploying a solution on Ansible to securely monitor all the Amazon EBS volumes attached on all the Amazon EC2 instances. the solution detects low disk space utilization, send alerts, and increase the volume size proactively.

## Key highlights of the solution
1. Utilizing existing configuration management tool - Ansible.
2. Securely stores IAM credentials and uses fine-grained access control to provide the least required access.
3. Utilize AWS APIs.
4. Gathers Amazon EBS volume data from all the Amazon EC2 instances.
5. Scalable solution as it can manage resources across regions and AWS accounts.
6. Proactively increase the volume size by 10% if no action is taken 1 hour after the alert.
