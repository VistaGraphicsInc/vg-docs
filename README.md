# VistaGraphics Inc. Documentation  

Create folder and README doc for:  
* Website going live  
* Drupal 7 install on AWS Elastic Beanstalk  

***  

### Table of Contents:  
* ipsum  
* lorem  
* schwing  

***  

## Drupal 7 Install on AWS Elastic Beanstalk  
### Specific to Installing Purchased Theme (theMag a.k.a. pinkdexo)  
Rough draft of steps below.  
Make into *official* follow-along doc for process replication.  

First test: http://cova-magazine.xkp4phxgmf.us-east-1.elasticbeanstalk.com  

1. Follow instructions for "Launch a DB instance in Amazon RDS"  
2. Follow instructions for "Launch an Elastic Beanstalk Environment"  
3. Follow instructions for "Configure Security Settings and Environment Properties"  
4. Download, extract and configure TheMag theme for Drupal 7  
  - download TheMag zip  
  - extract TheMag zip  
  - copy themag_drupal_7/themag_drupal_instalation folder to desktop and rename  
  - download version 1.0 https://github.com/aws-samples/eb-php-drupal/releases and extract its content  
  - copy all contained files and the .ebextensions folder in the top level of the renamed "themag_drupal_instalation" folder  
  - modify the configuration files  
    - .ebextensions/dev.config – restricts access to your environment to your IP address to protect it during the Drupal installation process. Replace the placeholder IP address near the top of the file with your public IP address.  
    - .ebextensions/efs-create.config – creates an EFS file system and mount points in each Availability Zone / subnet in your VPC. Identify your default VPC and subnet IDs  
    
5. Use terminal to navigate to the copied "themag_drupal_instalation" folder you renamed  
6. Use this command to zip the folder `zip ../drupal-beanstalk.zip -r * .[^.]* -x "vendor/*"`  
7. Upload and deploy your newly zipped folder to the environment you created before  
8. Navigate to your environments URL and complete the drupal installation steps  
9. If you wish to use the demo content  
  - In the drupal admin panel at the top, navigate to Configuration/System/Back up and Migrate/Restore  
  - Upload the file in "themag_demo_content"  
  
***  

`11/2/2018`  

* Be sure to follow steps from README.md
  - from `aws-samples`  
  
Copy the variables `.ebextensions settings` to settings.php after installing Drupal via `example-website/install.php`  

Applications deployed on Beanstalk hould be **stateless**  

***  

## Beanstalk Environment - Round 2  

#### Local_project_Name/Drupal_Folder:  
`export PATH=LOCAL_PATH_TO_EB.EXE`  

`eb init --platform "php 7.2" --region us-east-1`  

`eb init`  

"newkeypair.pem"  

default names for all aws resources  

#### dev.config  
```  

```  

***  

## S3 File System Module  

* current theme already has `libraries`  
* install AWS SDK for PHP  


