# Beginner - AWS (by dax)

* **Category:** AWS
* **Points:** 5

## Challenge

> The text of 
> the challenge.
> 01 - AWS whoami       
> In AWS, a user needs to generate an access key and a secret key  to interact with the AWS API. Can you find out to whom this set of  credentials belongs to?
 > Access key: AKIASECYGINVRUUGIJS6
 > Secret key: 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
 > Note: The us-east-1 AWS region is to be used for all challenges in this category.

## Solution

    ┌─[✗]─[user@parrot]─[~]
    └──╼ $aws configure
    AWS Access Key ID [None]: AKIASECYGINVRUUGIJS6
    AWS Secret Access Key [None]: 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
    Default region name [None]: us-east-1
    Default output format [None]: json
    
    ┌─[user@parrot]─[~]
    └──╼ $aws sdb list-domains --region us-east-1
    
    An error occurred (AuthorizationFailure) when calling the ListDomains operation: User (arn:aws:iam::146213847915:user/HF-hiykoWcaxgA2qK46IeZKpk1lOjPZc0Dp) does not have permission to perform (sdb:ListDomains) on resource (arn:aws:sdb:us-east-1:146213847915:domain/). Contact account owner.

```
HF-hiykoWcaxgA2qK46IeZKpk1lOjPZc0Dp
```
