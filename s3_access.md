##### To add a file to S3 using Python

```python
import boto3
from botocore.exceptions import NoCredentialsError

ACCESS_KEY = 'xxxxxxxxxxxxx'
SECRET_KEY = 'xxxxxxxxxxxxxxxxxxx'

def upload_to_aws(local_file, bucket, s3_file):
    s3 = boto3.client('s3', aws_access_key_id=ACCESS_KEY,
                      aws_secret_access_key=SECRET_KEY)

    try:
        s3.upload_file(local_file, bucket, s3_file)
        print("Upload Successful")
        return True
    except FileNotFoundError:
        print("The file was not found")
        return False
    except NoCredentialsError:
        print("Credentials not available")
        return False


uploaded = upload_to_aws(file_name_local, s3_bucket, file_name_s3)
```

##### To download a file from S3 

```python
s3 = boto3.client('s3', aws_access_key_id=ACCESS_KEY,
                      aws_secret_access_key=SECRET_KEY)
s3.download_file(s3_bucket_name, file_name_s3, file_name_local)
```
