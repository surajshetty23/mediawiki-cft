# MediaWiki
The Cloudformation template installs MediaWiki on AWS-Amazon Linux. As part of the installation the following packages are installed:
 - MySQL
 - PHP 
 - Apache

# Prerequisites
 - Create an AWS key-pair
 - To run the Cloudformation templates from command line, install the AWS CLI packages:
    - For Windows, install the AWS CLI using the MSI installer: https://awscli.amazonaws.com/AWSCLIV2.msi
    - For Linux, install the AWS CLI package

# Template Details
The template does the following:
  - Security Group
      - Allow 80 Inbound (HTTP)
      - Allow 22 Inbound (SSH)
  - EC2 Instance
      - Install MariaDB
      - Install PHP
      - Install Apache
      - Configure database
      - Download Mediawiki-1.35.1 packages
      - Configure Mediawiki
      - Restart Apache
    
 # Installation
  - Configure the parameters/mediawiki.json and update the following parameters:
      - KeyName        - The AWS key-pair generated.
      - DBUser         - Database Username for Mediawiki
      - DBPassword     - Database Password for Mediawiki
      - DBRootPassword - Root Password for database
  - Run the following command to start the installation <br/>
    aws cloudformation create-stack --stack-name mediawiki --template-body file://mediawiki.yml --profile mediawiki_setup --parameters file://property/mediawiki.json
  - After successful installation, the Mediawiki URL is published.
