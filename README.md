# AWSNotes
Useful notes on AWS, Boto3 and CDK


## Windows Scripts
### SSH to an EC2 Instance
```
@echo off
set target=%1
shift
@echo SSHing to AWS instance as %AWS_PROFILE%
aws ssm start-session --target %target%
```

### SSO Login
```
@echo off
set profile=%1
shift
if not defined profile set profile=a-default-profile
@echo Logging into AWS as %profile%
aws sso login --profile %profile%
set AWS_PROFILE=%profile%
```

### Tunnel To an EC2 Instance
```
@echo off
set target=%1
shift
@echo SSHing to AWS instance as %AWS_PROFILE%
aws ssm start-session --target %target% --document-name AWS-StartPortForwardingSession --parameters "{\"portNumber\": [\"8000\"], \"localPortNumber\": [\"8000\"]}"
```
