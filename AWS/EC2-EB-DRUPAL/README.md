# Drupal 7 Install on AWS Elastic Beanstalk  

## EC2 and Autoscaling with Elastic Beanstalk, RDS and S3 File Storage Drupal Install  

*Specific to Installing a Purchased Theme,* pinkdexo (in our case, a.k.a. theMag)  

Latest environment: http://covamagazinevg.us-east-1.elasticbeanstalk.com/  

A quick *one-two* high-level steps below.  

### AWS - EC2, EB, Drupal Install with S3FS  
1. Download [EB-PHPDrupal-1.0](https://github.com/aws-samples/eb-php-drupal/releases)  
2. Follow Instructions in **ReadMe.txt** (download the zips instead of using curl and wget)  
3. Once you have completed the steps in the **ReadMe.txt**, download [S3FS](https://www.drupal.org/project/s3fs)​ and its dependencies.  
4. Rename the AWS SDK to awssdk2 in the **sites/all/libraries** directory  
5. Follow the instructions in the S3FS ReadMe.txt  

### Configure proxy settings for S3 sync  
1. In the **.ebextensions** directory, create a new file (e.g. s3-proxy.config)  
2. Add the following code below to the file and then run `eb deploy`  

#### s3-proxy.config:  
```html
packages:
  yum:
    mod24_ssl: []

files:
  "/etc/httpd/conf.d/s3_proxy.conf":
    mode: "000644"
    owner: root
    group: root
    encoding: plain
    content:
        <ifModule mod_ssl.c>
            ProxyRequests Off
            SSLProxyEngine on
            <Proxy *>
                Order deny,allow
                Allow from all
            </Proxy>
            ProxyPass /s3fs-css/ https://bucketname.s3.amazonaws.com/s3fs-public/
            ProxyPassReverse /s3fs-css/ https://bucketname.s3.amazonaws.com/s3fs-public/
            ProxyPass /s3fs-js/ https://bucketname.s3.amazonaws.com/s3fs-public/
            ProxyPassReverse /s3fs-js/ https://bucketname.s3.amazonaws.com/s3fs-public/
        </ifModule>
```  
