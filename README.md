# MLOps_SageMaker
Coursera - MLOps Platforms: Amazon SageMaker and Azure ML

# Module 1
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



### Click the command prompt icon to open AWS CloudShell, under 'Actions' dropdown:

> select 'Delete AWS CloudShell home directory' to remove every you have done previously.

> select 'new tab', to add an extra AWS CloudShell in a new tab.

> select 'split into rows', to add an extra AWS CloudShell vertically.

> select 'split into columns' to add an extra AWS CloudShell horizontally.

> allow 'upload file' and 'download file'.

> 
