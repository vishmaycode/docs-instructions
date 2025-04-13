# Beginers Guide to setting up AWS account

### Reference Video 
 - [https://www.youtube.com/watch?v=CjKhQoYeR4Q](https://www.youtube.com/watch?v=CjKhQoYeR4Q)

### Account creation

Create a new root account by going to the link [https://aws.amazon.com/free](https://aws.amazon.com/free) using basic support free plan
upon login save the account id and other details to protonpass
then setup mfa using google authenticator

then go ahead and create a new user in IAM - users
 - provide user access to aws management console 
 - create an iam
 - custom password
 - uncheck "user must create a new password on next sign-in"
 - attach policies directly
 - administrator access
save the url to bookmark so it will be easy to login next time

### Setting up Billing Alarms

 - [https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html)
  
##### Enable billing alerts
 - Then go to aws billing console
 - chose billing preferences - billing alerts
 - edit alert preferences
 - check receive aws free tier alerts and receive cloudwatch billing alerts & update

##### Create billing alerts in Cloudwatch

 - go to cloudwatch link in docs [https://console.aws.amazon.com/cloudwatch/](https://console.aws.amazon.com/cloudwatch/)
 - click on create alarms
 - change region to - us-east-1 N virgenia
 - create alarm
 - select matrix
 - chose billings
 - total estimated charges
 - select USD and hit Select Matrix
 - leave defaults only edit threshold to 2 dollers & next
 - under notifications - add notification
 - create a new topic - billing alarm topic and add email ids & next
 - add alarm name and next - create alarm
 - also confirm email from spam box for subscription


### Setup AWS CLI

Hit [https://aws.amazon.com/cli/](https://aws.amazon.com/cli/)

```shell
cd ~/Downloads
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install --bin-dir /usr/local/bin --install-dir /usr/local/aws-cli --update
```

then go back to security credentials on your account in browser
then go down to access keys and create a new key
set it for aws cli and leave description blank
then you will have a secret key
then on your desktop terminal do this
```shell
aws configure
```
and enter the access key and secret access key into it
also set region to ap-south-1 and output format to json

Testing - this should not return any error
```shell
aws s3 ls
```
