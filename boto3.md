### Create S3 bucket using python-boto3
- Create a file in the EC2 instance create_bucket.py and as the below code.
- `sudo nano create_bucket.py`
```import logging
import boto3
from botocore.exceptions import ClientError


def create_bucket(bucket_name, region=None):
    """Create an S3 bucket in a specified region

    If a region is not specified, the bucket is created in the S3 default
    region (us-east-1).

    :param bucket_name: Bucket to create
    :param region: String region to create bucket in, e.g., 'us-west-2'
    :return: True if bucket created, else False
    """

    # Create bucket
    try:
        if region is None:
            s3_client = boto3.client('s3')
            s3_client.create_bucket(Bucket=bucket_name)
        else:
            s3_client = boto3.client('s3', region_name=region)
            location = {'LocationConstraint': region}
            s3_client.create_bucket(Bucket=bucket_name,
            CreateBucketConfiguration=location)
    except ClientError as e:
        logging.error(e)
        return False
    return True
bucket_name=input("Bucket name: ")
region=input("Bucket region: ")
create_bucket(bucket_name, region)
```
#### Output:

![image](https://user-images.githubusercontent.com/97250268/199938966-eb1f595e-769b-49e5-9ff1-40b99bd24bac.png)

#### Bucket got created in aws :
- Bucket got created in specified region

![image](https://user-images.githubusercontent.com/97250268/199939263-f10ac8cd-ffdb-40c5-b3ef-376078c0c3c8.png)



 
### Upload data/file to S3 bucket using python boto3

- Create python file (upload_file.py) and add below code:
- `sudo nano upload_file.py`
- Create one .txt file in EC2 instance if you have nothing to upload
 ```
import logging
import boto3
from botocore.exceptions import ClientError


def upload_file(file_name, bucket, object_name=None):
    """Upload a file to an S3 bucket

    :param file_name: File to upload
    :param bucket: Bucket to upload to
    :param object_name: S3 object name. If not specified then file_name is used
    :return: True if file was uploaded, else False
    """

    # If S3 object_name was not specified, use file_name
    if object_name is None:
        object_name = file_name

    # Upload the file
    s3_client = boto3.client('s3')
    try:
        response = s3_client.upload_file(file_name, bucket, object_name)
    except ClientError as e:
        logging.error(e)
        return False
    return True

file_name=input("Name of file you would like to upload: ")
bucket=input("Name of bucket to upload to: ")
upload_file(file_name, bucket)
```

#### Output:

![image](https://user-images.githubusercontent.com/97250268/199939489-b43afec8-9ec2-412b-b484-d88ad1dd5ad4.png)

#### File got uploaded in the bucket mentioned:

![image](https://user-images.githubusercontent.com/97250268/199939932-3f6d3bc8-c90e-40e4-b448-15c8d4c13ed1.png)


### Download Files from Bucket:

- This downloads the file from the bucket to EC2 instance
- Create python file `sudo nano download_file` and add the below code
```import boto3

s3 = boto3.client('s3')

BUCKET_NAME=input("What is the name of the bucket you want to rerieve: ")
FILE_NAME=input("What is the name of the file you want to retrieve: ")
OBJECT_NAME=FILE_NAME

s3.download_file(BUCKET_NAME, OBJECT_NAME, FILE_NAME)
```
#### Output:

![image](https://user-images.githubusercontent.com/97250268/200058071-fd7e37c4-ea96-4adf-a996-5de067ae1397.png)

### Delete Bucket:

- Make sure your bucket is empty .
- Create python file  `sudo nano delete_bucket.py` and add

```
import boto3

s3 = boto3.client('s3')

bucket=input("What is the name of the bucket you would like to delete: ")

response = s3.delete_bucket(Bucket=bucket)
```

#### Output:

![image](https://user-images.githubusercontent.com/97250268/200058699-a31d3ea4-8ae0-4b96-8448-4de987290223.png)

