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