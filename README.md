
# secure-S3FS
A secure Amazon S3 Based File System

Prerequisites
-------------

| Software    | Version     |
| ----------- | ----------- |
| `openssl`   | [`1.0.2o`](https://www.openssl.org/source/)|
|`automake`|`latest`|
|`pkg-config`|`latest`|

Setup for Secure-S3FS
----------------------
*	Create an AWS Account if you don’t already have one refer to AWS Documentation 
	https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/
*	Navigate to S3 bucket from AWS console
*	Create a bucket (remember bucket name has to be unique)
*	Acquire your credentials from AWS account (IAM)

Enter S3 identity and credential in a file ~/.passwd-s3fs 
---------------------------------------------------------
```
    echo ACCESS_KEY:SECRET_KEY > ~/.passwd-s3fs
    chmod 600 ~/.passwd-s3fs
```


Clone the secure-S3FS and configure it
--------------------------------------------------------------
```
    git clone https://github.com/Joy57/secure-S3FS.git
    cd secure-S3FS
    ./autogen.sh
    ./configure
    make
    sudo make install
```

Troubleshoot for Mac
--------------------------------------------------------------
If you get the error: 

`./configure: line 4965: syntax error near unexpected token common_lib_checking,
./configure: line 4965: PKG_CHECK_MODULES(common_lib_checking, fuse >= ${min_fuse_version} libcurl >= 7.0 libxml-2.0 >= 2.6 )'`

Make sure the following packages are installed.
```
    brew install automake
    brew install pkg-config
    brew install libssl-dev
```
and then run

```
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

