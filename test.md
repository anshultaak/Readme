Backup Plan

Prerequisites:
Ensure the following packages are installed:
- Git
- AWS CLI
- Terraform

Configure AWS CLI:
1. Open your terminal and navigate to your home directory.
2. Edit the AWS credentials file:
```bash
cd ~
vi ~/.aws/credentials
```
3. Paste your AWS secret and access keys into the file:
```plaintext
[ps_aws]
aws_access_key_id=*******************
aws_secret_access_key=*******************************
```
Replace `*******************` and `*******************************` with your actual keys.

Clone the Terraform Repository from GitHub:
1. Clone the repository:
```bash
git clone https://mindnerves1@bitbucket.org/mindnerves_technologies/medibuddy-teraform.git
```
2. Navigate into the repository directory:
```bash
cd medibuddy-teraform
```

Update Terraform Variables:
1. Update the EC2 latest AMI and RDS snapshot identifier in `terraform.tfvars` file:
```bash
vi terraform.tfvars
```
2. Update the variables:
```plaintext
ec2_ami="<your_ami_id>"
Rds_snapshot="<your_snapshot_identifier>"
```
Replace `<your_ami_id>` and `<your_snapshot_identifier>` with the appropriate values.

Create the New Infrastructure:
1. Initialize Terraform within the repository directory:
```bash
terraform init
```
2. Review the execution plan:
```bash
AWS_PROFILE=ps_aws terraform plan -var-file=terraform.tfvars
```
3. Apply the Terraform configuration to create the infrastructure:
```bash
AWS_PROFILE=ps_aws terraform apply -var-file=terraform.tfvars
```
Add the new EC2 IP in RDS Security Group for Connection

Please review the screenshot below for the backup EC2 and RDS.

