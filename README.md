# Static Website Deployment on AWS EC2 using Apache

This README provides detailed steps on how to deploy a static website on an AWS EC2 instance using Apache.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Setup AWS EC2 Instance](#setup-aws-ec2-instance)
- [Install and Configure Apache](#install-and-configure-apache)
- [Deploy the Static Website](#deploy-the-static-website)
- [Access the Website](#access-the-website)
- [Conclusion](#conclusion)

## Introduction

This guide will walk you through the process of deploying a static website on an AWS EC2 instance using Apache. 
The static website includes an HTML file hosted on GitHub. The website will mention the HNG Internship and contain a link to [https://hng.tech](https://hng.tech).

## Prerequisites

- An AWS account
- Basic knowledge of AWS EC2 and SSH
- An SSH key pair for accessing the EC2 instance
- A static website (HTML, CSS, JavaScript files)

## Setup AWS EC2 Instance

1. **Launch an EC2 Instance**:
    - Log in to your AWS Management Console.
    - Navigate to EC2 Dashboard.
    - Click on "Launch Instance".
    - Choose an Amazon Machine Image (AMI) (e.g., Amazon Linux 2 AMI).
    - Select an Instance Type (e.g., t2.micro for free tier eligibility).
    - Configure Instance Details (default settings are usually fine).
    - Add Storage (default settings are fine).
    - Add Tags (optional).
    - Configure Security Group:
      - Add a rule to allow HTTP traffic on port 80.
      - Add a rule to allow SSH traffic on port 22.
    - Review and Launch the instance.
    - Select your SSH key pair for the instance.

2. **Connect to the EC2 Instance**:
    - Open a terminal (or use PuTTY if on Windows).
    - Connect to your instance using SSH:
      ```sh
      ssh -i /path/to/your-key-pair.pem ec2-user@your-instance-public-ip
      ```

## Install and Configure Apache

1. **Update Packages**:
    ```sh
    sudo yum update -y
    ```

2. **Install Apache**:
    ```sh
    sudo yum install httpd -y
    ```

3. **Start Apache**:
    ```sh
    sudo systemctl start httpd
    ```

4. **Enable Apache to Start on Boot**:
    ```sh
    sudo systemctl enable httpd
    ```

## Deploy the Static Website

1. **Navigate to the Apache Directory**:
    ```sh
    cd /var/www/html
    ```

2. **Download the `index.html` File Using `wget`**:
    ```sh
    sudo wget https://raw.githubusercontent.com/AugustHottie/devops-task0/master/index.html
    ```

3. **Set the Correct Permissions**:
    ```sh
    sudo chown apache:apache /var/www/html/index.html
    sudo chmod 644 /var/www/html/index.html
    ```

## Access the Website

1. **Open a Web Browser**:
    - Navigate to the public IP address of your EC2 instance. Your static website should be displayed.

## Conclusion

By following the steps outlined in this guide, you have successfully deployed a static website on an AWS EC2 instance using Apache. 
Your website should now be accessible via the public IP address of your EC2 instance.
