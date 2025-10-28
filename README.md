# ansibleebsautomation

This repository provides a guide to deploying a solution on Ansible using a Dynamic Inventory that collects information about all EC2 instances with public IPs across all AWS regions.

Modifying the configuration from
`ansible_host: public_ip_address` to `ansible_host: private_ip_address`
will enable the host to SSH into EC2 instances using their private IPs. However, this will only work if the Ansible control node can access those instances over private IP (for example, if it’s in the same VPC).

The solution uses Ansible Vault to securely store IAM credentials and continuously monitors disk utilization on EC2 instances. If the usage exceeds a defined threshold (e.g., 85%), it sends alerts using Amazon SNS.

**At a high level**, this solution leverages a CloudFormation template to create an AWS programmatic user with permissions to list EC2 instances (for inventory management) and publish messages to an SNS topic. The CloudFormation stack also creates the SNS topic and subscription.

The Ansible configuration securely stores credentials using Ansible Vault, connects to EC2 instances using public IPs (configurable for private IPs), monitors disk utilization every hour, and sends alerts via SNS if the threshold is crossed.

---

## Schedule the playbook to run every hour

```bash
crontab -e
```
```bash
0 * * * * /usr/bin/ansible-playbook -i ./aws_ec2.yml ./disk_monitor.yml -u ec2-user --key-file ./mykey.pem >> /var/log/ansible_disk_monitor.log 2>&1
```
