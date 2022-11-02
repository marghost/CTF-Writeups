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

* https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#cliv2-linux-install

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

* https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html

### Flag

```
HF-eYCTnr7FGTwrIlRGMMa5RoQvPVloC7Vu
```

## 03 - AWS ls and cp 

* **Category:** AWS
* **Points:** 7

### Challenge
     
> AWS S3 (Simple Storage Service) can be used to store files in a  bucket like in a regular file system's folder. Using the credentials  given in the AWS whoami challenge, can you recover the flag from the  following bucket?
> hf-aws-beginner-challenge3-bucket-146213847915

### Solution

    ┌─[✗]─[user@parrot]─[~]
    └──╼ $aws s3 cp s3://hf-aws-beginner-challenge3-bucket-146213847915/flag.txt flag.txt
    download: s3://hf-aws-beginner-challenge3-bucket-146213847915/flag.txt to ./flag.txt

    ┌─[user@parrot]─[~]
    └──╼ #cat flag.txt 
    HF-9kYVaWfBcCRVPqGbgGeUoQFHgCsUbgbh

### Doc

* https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/cp.html  

### Flag

```
HF-9kYVaWfBcCRVPqGbgGeUoQFHgCsUbgbh
```

## 04 - AWS mongodump

* **Category:** AWS
* **Points:** 8

### Challenge
     
> AWS DynamoDB provides a fast key/value store similar to a MongoDB  collection. Using the credentials given in the AWS whoami challenge,  can you recover the flag from the following table?
> hf-aws-beginner-challenge4-table

### Solution

    ┌─[✗]─[user@parrot]─[~]
    └──╼ $aws dynamodb scan --table-name hf-aws-beginner-challenge4-table --output text
    None    1       1
    FLAG    HF-lsJkjJAaD9cDCGi2LvDnAmY1KHJMuuZ6

### Flag

```
HF-lsJkjJAaD9cDCGi2LvDnAmY1KHJMuuZ6
```

## 05 - AWS sudo

* **Category:** AWS
* **Points:** 9

### Challenge
     
> In AWS, you can assume different roles to interact with the AWS  API as another resource. For example, you could assume the role of a  Lambda function you created to troubleshoot its permissions. Using the  credentials given in the AWS whoami challenge, can you assume the role arn:aws:iam::146213847915:role/hf-aws-beginner-challenge5-role and run the following command?
> aws ssm get-parameter --name hf-aws-beginner-challenge5-parameter

### Solution

    aws sts assume-role --role-arn "arn:aws:iam::146213847915:role/hf-aws-beginner-challenge5-role" --role-session-name AWSCLI-Session
      
    AWS_ACCESS_KEY_ID=ASIASECYGINVZOODKAV5 AWS_SECRET_ACCESS_KEY=4/bRKmyOqk+hlGGo5tmDwUvy5heKefOsBV0Eq3go AWS_SESSION_TOKEN=IQoJb3JpZ2luX2VjEGYaCXVzLWVhc3QtMSJGMEQCIDcvpXl9eLKlmwW0/o0M66Z7ikuFODsO0rYyYRFqr0B2AiAKMiDrqBokwICviBiZOvrNGXuWWiw6gv/Q9cVJv8TdCyqbAghPEAIaDDE0NjIxMzg0NzkxNSIMawtCH+2+qWchBRmVKvgB673BqP+5KHlbNckF5mgU3EHg1EgdBxLuzqfIYKUxFPKqKO2xA4ZFP+W8Zv8qO3S73pEPXS4NHdeh9n3Ol54wqFSLKLWpIDikorzsui8r0/XRQIds78y/BMpxkurlrTBhgjdRLfUb/MKS+57b+kNecs+lMu5WA+zMo8mn4NEs0oahfFr22YtcYxSTB9rw3uygsqyapPYqTKEYMr/oj+0g5gL9gS5U5gvMVUzEbjnTWD4VKjwlZX23laEGukSwxmuC8WxWmVlQkkOC24IN9RcqivO6HulOM4Mjdmd8Lao2sLhc7Mr1AN3RO6JjfP12ze3y1/xbRxO9snEwi8P2mgY6ngFVcoXR6CKhupERunlRrHm6DcExCdBIjzM3DafaRN92IUwaljPI31WMrJwo3xfJCnm5Nz5TRUvh++Qi39dEsR4qEiM/fvcgbHyBsCeMkeqpNjhPjCZ+dwzp85ym56w9UkAxylJpzrmJqGs6beMQYGtGWQuinn2Qv8HUDhGnVL71ZqDp9BuRgJvMoytRlypERUiVdA+lAGXGy+D5KfLWKw== aws ssm get-parameter --name hf-aws-beginner-challenge5-parameter
    
    {
        "Parameter": {
            "Name": "hf-aws-beginner-challenge5-parameter",
            "Type": "String",
            "Value": "HF-jJeRqCAQGsDLoV4PcFPKWFXTzWhbkvXU",
            "Version": 1,
            "LastModifiedDate": "2022-10-19T23:30:40.537000+01:00",
            "ARN": "arn:aws:ssm:us-east-1:146213847915:parameter/hf-aws-beginner-challenge5-parameter",
            "DataType": "text"
        }
    }

### More info

If need be you can reset the access key and token with those commands

    ┌─[user@parrot]─[~]
    └──╼ $unset AWS_ACCESS_KEY_ID 
    ┌─[user@parrot]─[~]
    └──╼ $unset AWS_SE
    AWS_SECRET_ACCESS_KEY  AWS_SESSION_TOKEN      
    ┌─[user@parrot]─[~]
    └──╼ $unset AWS_SESSION_TOKEN 
    ┌─[user@parrot]─[~]
    └──╼ $unset AWS_SECRET_ACCESS_KEY 
    ┌─[user@parrot]─[~]
    └──╼ $aws configure
    AWS Access Key ID [****************IJS6]: AKIASECYGINVRUUGIJS6
    AWS Secret Access Key [****************DKlH]: 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
    Default region name [us-east-1]: us-east-1
    Default output format [json]: json

### Doc

* https://aws.amazon.com/premiumsupport/knowledge-center/iam-assume-role-cli/

### Flag

```
HF-jJeRqCAQGsDLoV4PcFPKWFXTzWhbkvXU
```

## 06 - AWS curl

* **Category:** AWS
* **Points:** 10

### Challenge
     
> In AWS, the access to some publicly accessible resources (such as  an S3 Bucket or an API Gateway) can be restricted using a signature  mechanism. This signature can be generated using a set of AWS  credentials and a library such as Python's AWSRequestsAuth. Some tools,  such as Postman, even integrate this signature mechanism in their  supported authentication methods. Using the credentials given in the AWS  whoami challenge, can you recover the flag the following URL? https://1f1xwaoef4.execute-api.us-east-1.amazonaws.com/api/

### Solution

N/A

### Flag

```

```
 