# Beginner - AWS (by dax)

## 01 - AWS whoami  

* **Category:** AWS
* **Points:** 5

### Challenge
     
> In AWS, a user needs to generate an access key and a secret key  to interact with the AWS API. Can you find out to whom this set of  credentials belongs to?
 > Access key: AKIASECYGINVRUUGIJS6
 > Secret key: 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
 > Note: The us-east-1 AWS region is to be used for all challenges in this category.

### Solution

    ┌─[✗]─[user@parrot]─[~]
    └──╼ $aws configure
    AWS Access Key ID [None]: AKIASECYGINVRUUGIJS6
    AWS Secret Access Key [None]: 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
    Default region name [None]: us-east-1
    Default output format [None]: json
    
    ┌─[user@parrot]─[~]
    └──╼ $aws sdb list-domains --region us-east-1
    
    An error occurred (AuthorizationFailure) when calling the ListDomains operation: User (arn:aws:iam::146213847915:user/HF-hiykoWcaxgA2qK46IeZKpk1lOjPZc0Dp) does not have permission to perform (sdb:ListDomains) on resource (arn:aws:sdb:us-east-1:146213847915:domain/). Contact account owner.

### Doc

> https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#cliv2-linux-install

### Flag

```
HF-hiykoWcaxgA2qK46IeZKpk1lOjPZc0Dp
```

## 02 - AWS cat mysecrets.txt 

* **Category:** AWS
* **Points:** 6

### Challenge
     
> In AWS, Secrets Manager can act as a sort of password manager for  your applications, and access to those secrets can be logged and  restricted. Using the credentials given in the AWS whoami challenge, can  you recover the flag stored it the following secrets manager's secret?
> hf-aws-beginner-challenge2-secret

### Solution

    ┌─[✗]─[user@parrot]─[~]
    └──╼ $aws secretsmanager get-secret-value --secret-id hf-aws-beginner-challenge2-secret
    {
        "ARN": "arn:aws:secretsmanager:us-east-1:146213847915:secret:hf-aws-beginner-challenge2-secret-1ZcN0L",
        "Name": "hf-aws-beginner-challenge2-secret",
        "VersionId": "88694825-9080-49ad-a01f-c22cc08f79ab",
        "SecretString": "HF-eYCTnr7FGTwrIlRGMMa5RoQvPVloC7Vu",
        "VersionStages": [
        "AWSCURRENT"
    ],
    "CreatedDate": "2022-10-19T23:30:40.248000+01:00"
    }

### Doc

> https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html

### Flag

```
HF-eYCTnr7FGTwrIlRGMMa5RoQvPVloC7Vu
```
