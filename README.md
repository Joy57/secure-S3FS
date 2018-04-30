
# secure-S3FS
A secure Amazon S3 Based File System

Setup for Secure-S3FS
----------------------
•	Create an AWS Account if you don’t already have one refer to AWS Documentation 
	https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/
•	Navigate to S3 bucket from AWS console
•	Create a bucket (remember bucket name has to be unique)
•	Acquire your credentials from AWS account (IAM)

Enter S3 identity and credential in a file ~/.passwd-s3fs 
---------------------------------------------------------
```
    echo ACCESS_KEY:SECRET_KEY > ~/.passwd-s3fs
    chmod 600 ~/.passwd-s3fs
```
Get the secure-S3FS from my github repository and configure it
--------------------------------------------------------------
```
    git clone https://github.com/Joy57/secure-S3FS.git
    cd secure-S3FS
    ./autogen.sh
    ./configure
    make
    sudo make install
```
Run with the bucket you created earlier
----------------------------------------
```
    mkdir /path/to/mountpoint

    s3fs mybucket /path/to/mountpoint -o passwd_file=~/.passwd-s3fs

    cd /path/to/mountpoint
```
Note to change password for encryption/decryption in s3fs.
----------------------------------------------------------
There's a file in the src folder which is called `secret.txt`. Open it and change it to the password you'd like. 

