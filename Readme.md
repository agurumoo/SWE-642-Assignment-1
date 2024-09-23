AWS Website Deployment: S3 and EC2

AWS Account Setup
Create an AWS Account:
I signed up for an AWS account and completed the credit card verification process.

S3 Deployment (Static Website Hosting)
1. In the AWS Management Console, I navigated to the S3 service and created a bucket named agurumoo.
2. I uploaded my website files (HTML, CSS, JS, images) by dragging and dropping them into the agurumoo bucket.
3. In the Properties tab of the bucket, I enabled Static website hosting and set index.html as the index page.
4. To allow public access and ensure that my images and other files load correctly, I updated the bucket policy using the following JSON:
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Effect": "Allow",
                "Principal": "*",
                "Action": "s3:GetObject",
                "Resource": "arn:aws:s3:::agurumoo/*"
            }
        ]
    }
5. After configuring the bucket, I copied the S3 website URL and pasted it into my browser to verify the deployment:
    S3 URL: https://agurumoo.s3.us-east-2.amazonaws.com/index.html


EC2 Deployment (Linux Server Hosting)
1. I navigated to EC2 in the AWS Console and launched a new instance.
    I chose the Amazon Linux 2 AMI, named the instance agurumoo, and created a key pair for secure access.
2. Once the instance passed the health checks, I clicked Connect from the EC2 dashboard and used EC2 Instance Connect to open a terminal.
3. I went into the Security Group settings for my EC2 instance and added inbound rules to allow traffic:
    I added rules for HTTP (port 80) and HTTPS (port 443), allowing traffic from anywhere (0.0.0.0/0).
4. I switched to the root user for administrative privileges by running:
    sudo su -
5. I created a directory to store my website files:
    mkdir swe642
    cd swe642
    mkdir Assign1
    cd Assign1
6. I uploaded my project to GitHub and used the following commands to download and extract the files:
    wget https://github.com/agurumoo/SWE-642-Assignment-1.git
    wget https://github.com/agurumoo/SWE-642-Assignment-1/archive/refs/heads/main.zip
    unzip main.zip
    cd SWE642_Ass1-main/
7. I moved the files to the web directory:
    mv * /var/www/html/
8. Finally, I accessed my website using the public IP address (18.222.149.127) of my EC2 instance:
    EC2 Public IP: http://18.222.149.127

