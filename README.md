1. Create AWS account && log in AWS (top right corner choose your <nearest region>)
2. Select EC2 && chose "Launch instance"
3. Name your server && in image search menu type (Centos stream 9)
4. From the AWS market AMIs select Centos stream 9 latest
5. Select instance type (First month some of the instances ex: *t3.micro* are free)
6. In the KEY PAIR step, select *create new key pair*, enter key name and press Create key pair (let RSA and Keyformat by default). Generated key will automatically download on your PC.
7. Network settings chek mark ALLOW HTTPS and HTTP
8. Configure storage, all setting by default.
9. Finally press LAUNCH INSTANCE

#######################################################

Post instance creation actions:
1. chmod 600 <path_to_your_key>/<key_name.pem>

#######################################################

Connecting to the instance:
ssh -i <path_to_your_key>/<key_name.pem> ec2-user@<instance_public_ip>

#######################################################

Installing MySQL 8
1. sudo dnf upgrade --refresh -y
2. sudo dnf install mysql mysql-server git -y
3. sudo systemctl enable mysqld --now

How to connect to Local MySQL:
1. mysql -u root

#######################################################

1. Visual code (remote connect via SSH):
2. Install *Remote Development* plugin
3. Select *Remote Explorer* and add *ssh -i <path_to_your_key>/<key_name.pem> ec2-user@<instance_public_ip>

FYI for saving money, in the end of session stop your EC2 instance.