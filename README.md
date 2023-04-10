# MLOps_SageMaker
Coursera - MLOps Platforms: Amazon SageMaker and Azure ML

# Module 1
### Started with AWS ClouShell
Click the command prompt icon to open AWS CloudShell, under 'Actions' dropdown:

> select 'Delete AWS CloudShell home directory' to remove every you have done previously.

> select 'new tab', to add an extra AWS CloudShell in a new tab.

> select 'split into rows', to add an extra AWS CloudShell vertically.

> select 'split into columns' to add an extra AWS CloudShell horizontally.

> allow 'upload file' and 'download file'.

In AWS CloudShell (ie terminal), type:
>```conda env list``` to list out packages within an environment

>```nvidia-smi -l 1``` to show GPU specification and usage

>```aws s3 --help``` to show features on AWS cli for S3 

>```df -h``` to show used and available disk space

>```echo $SHELL``` will return ```/bin/bash```.  Then $```vim ~/.bashrc```, you can modify the setup file.

>```zsh``` then switch to ZSH environment.

>```aws s3api create-bucket <folder name> --region <region name>``` to create a S3 bucket.

>```aws s3 ls | wc -l``` to count number of files within a bucket.

>```#<text>```, CouldShell won't execute the text.

>```aws s3 sync . <S3 bucket name>``` to sync a local directory to S3 directory

>```zip -r <folder file to be zipped> <name of the zip file>``` to zip a directory


### Prototyping AI APIs in CouldShell
>```sudo yum install lynx```, Lynx is a library to browse internet in a terminal

>```lynx -dump <url> | less``` to browse internet in a terminal 

Example 1: To extract text from internet for sentiment analysis:

step 1: >```TEXT=`lynx -dump <url> | head -c 5000` ``` (limited to 5000 bytes)

step 2: >```echo $TEXT```

step 3: >```aws comprehend detect-sentiment --language-code "en" --text "$TEXT"```

Example 2: To detect entities from an internet page:

>```aws comprehend detect-entities --language-code "en" --text "$TEXT" --output text | cut -f 5 | tr -cd "[:alpha:][:space:]" | tr ' [:upper:]' '\n[:lower:]' | tr -s '\n' | sort | uniq -c | sort -nr -k 1 | head```

- go to https://github.com/noahgift/DotNetAWSComprehend for more examples

  
### Cloud9 with AWS CodeWhisperer
In Cloud9's terminal, type:
>```aws s3 ls help```
  
>```aws s3 ls | wc -l``` to count number of files within a bucket.

By clicking AWS icon on the left bar, under Explorer to integrate with other AWS services.  Under Developer Tools, CodeWhisperer is there.  Type the following to initate a VM:

Step 1: >```python3 -m venv ~/.venv && source ~/.venv/bin/activate```
  
Step 2: >```pip install boto3```
  
Step 3: >```pip install black```
  
Step 4: Go to the file tree on the left bar, type >```touch s3.py``` to create an empty .py file.  Then start typing the function description and import libraries.  Wait a bit and tab to complete code suggestions.

Step 5: In terminal, type >```black s3.py``` to enable colouring for code in s3.py.  This can be run multiple times during the coding process.
  
Step 6: Then, run the code by typing ```python s3.py``` in terminal to test the code.  Modify the code if necessary.
  
  
### Amazon Simple Storage Service (Amazon S3)

Bucket: ```https://s3-<aws-region>.amazonaws.com/<bucket-name>```  
  
Object: ```https://s3-<aws-region>.amazonaws.com/<bucket-name>/<object-key>```
  
Bucket names must be globally unique (3-63 characters long), accepting lowercase, numbers and hyphens (-) but not uppercase and underscores (_)
 
Useful for hosting a static website (must be enabled)
Structure: ```http://<bucket-name>.s3-website-<aws-region>.amazonaws.com```
Object: ```http://<bucket-name>.s3-<aws-region>.amazonaws.com/<object-key>```  

Use the PUT object to upload objects to S3.  For example, put core.css to the bucket:
```python
  import boto3
  S3API = boto3.client("s3", region_name="us-east-1"
  bucket_name = "samplebucket"
  filename = "/resources/website/core.css"
  S3API.upload_file(filename, bucket_name, "core.css", 
  ExtraArgs={'ContentType': "text/css", "CacheControl": "max-age=0"})
  ```

Use the GET object to retrieve objects from S3. 
  
If versioning disabled, the deleted object is permanently deleted from the bucket.  If versioning enabled, delete with only the object key.
  
S3 Select is a powerful tools to query data in place.
  
Data Encryption: Securing data in-transit vs securing data at rest
  
Access Control Lists (ACLs): identity-based policies vs resource-based policies
  

### AWS Storage Mediums
- Database: key-value database, graph database and Amazon Aurora (access via SQL)
  
- Data Lake: include Metadata, storage (built on top of S3) and compute
  
- AWS EFS (Elastic File System): connect with NFS (network file system is a distributed file system protocol that allows users to access files over a network like they access local storage) and Windows 
  
- AWS EBS (Elastic Block Storage is block-level storage solution used with the EC2 cloud service to store persistent data): Custom I/O and only available for a single mount point
  

 ### Working with Amazon S3
  
Within S3, select a file from a bucket.  Undert the 'Object actions' drop-down, select 'Query with S3 Select'.  Scroll down to 'SQL query' then run SQL query to inspect the object, with 'Raw' and 'Formatted' view. 
  
Alternatively, you can update a file via Cloud9 by typing:
>```aws s3 cp help | less | grep "aws s3 cp"``` to list out command examples
  

  
  

  

  

  




