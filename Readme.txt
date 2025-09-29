Step 1: Setting Up an S3 Bucket for Static Website Hosting

1.	Log in to AWS Console and navigate to S3.
2.	Click Create Bucket and provide a unique name.
3.	Select the AWS region of your choice.
4.	Uncheck Block all public access and acknowledge the warning.
5.	Enable Static website hosting under the Properties tab.
6.	Upload your HTML, CSS, and other website files.
7.	Set the necessary permissions:
             Go to the Permissions tab → Bucket Policy
             Add the following policy (replace YOUR-BUCKET-NAME):
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::ganesh-645-hw1/*"
    }
  ]
}
8.	Save and access your website using the Bucket website endpoint.

URL of S3 bucket website endpoint: https://ganesh-645-hw1.s3.us-east-1.amazonaws.com/index.html

Step 2: Setting Up an EC2 Instance

1.	Navigate to EC2 and click Launch Instance.
2.	Select an Amazon Machine Image (AMI) (e.g., Amazon Linux 2 or Ubuntu).
3.	Choose an instance type (e.g., t2.micro for free-tier eligibility).
4.	Configure the instance:
	     Add storage as needed.
5.	Launch the instance and download the .ppk key file.
6.	Connect to the instance 


Step 3: Deploying the Website on EC2


1.	Update system packages:
2.	sudo yum update -y  # For Amazon Linux
        sudo apt update -y  # For Ubuntu

3.	Install a web server (e.g., Apache):
4.	sudo yum install httpd -y  # For Amazon Linux
        sudo apt install apache2 -y  # For Ubuntu

5.	Start and enable the web server:
6.	sudo systemctl start httpd
        sudo systemctl enable httpd

7.	Copy your website files to /var/www/html/:
        sudo mv /path/to/your/project/* /var/www/html/

8.	Restart Apache:
         sudo systemctl restart httpd
9.	Access your website using the EC2 public IP.

ip address of Ec2 instance: 35.175.247.35



"Webhook test" 
