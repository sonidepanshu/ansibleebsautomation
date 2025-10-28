We will utilize the AWS CloudFormation template "access/iamusercloudformationtemplate.json" to create an IAM policy that grants a programmatic IAM user permission to list EC2 instances, and send SNS alerts to `ansiblealerts@deepanshu.com`.

### Step 1:
Open the AWS CloudFormation Console
Click on Create Stack, upload "access/iamusercloudformationtemplate.json", and create the stack as guided here: [+](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-create-stack.html)

### Step 2:
After the stack is created, login to your email account `ansiblealerts@deepanshu.com` and confirm the SNS alert `EBSalerts` subscriptions.

### Step 3:
On the Ansible control node, install Amazon AWS Collection[+](https://galaxy.ansible.com/ui/repo/published/amazon/aws/) and create a Vault file to store the AWS credentials by running the command below:
```bash
ansible-galaxy collection install amazon.aws
ansible-vault create ~/.aws/ansible_aws_credentials.yml
```
The command will prompt you to set a password.
After setting the password, add the credentials and save the file:
```yaml
aws_access_key: xxxxxxxxxxxxxxxx
aws_secret_key: xxxxxxxxxx/xxxxxx/xxxxxxxxxxxxxxx
```
