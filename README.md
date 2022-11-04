1. Create AWS account && log in AWS (top right corner choose your <nearest region>)
2. Select EC2 && chose "Launch instance"
3. Name your server && in image search menu type (Centos stream 9)
4. From the AWS market AMIs select Centos stream 9 latest
5. Select instance type (First month some of the instances ex: *t3.micro* are free)
6. In the KEY PAIR step, select *create new key pair*, enter key name and press Create key pair (let RSA and Keyformat by default). Generated key will automatically download on your PC.
7. Network settings chek mark ALLOW HTTPS and HTTP
8. Configure storage, all setting by default.
9. Finally press LAUNCH INSTANCE

Post instance creation actions:
1. chmod 600 <path_to_your_key>/<key_name.pem>

Connecting to the instance:
ssh -i <path_to_your_key>/<key_name.pem> <ec2-user@instance_public_ip>

Installing MySQL 8
1. sudo dnf upgrade --refresh -y
2. sudo dnf install mysql mysql-server -y
3. sudo systemctl enable mysqld --now

Creating MySQL database on AWS RDS.
1. Type RDS in AWS search menu, and select RDS
2. Select Databases and choose CREATE DATABASE
3. Select MySQL && Templates FREE TIER
4. Settings:
    a. Name your DATABASE
    b. Master userbame (by degaul: admin)
    c. Enter Master password
5. Instance config -> choose *db.t3.micro*
6. Storage: SET allocated storage 10GB, disable auto-scaling and SET maximum storage burst to 30GB
7. Connectivity: Select *Connect to an EC2 compute resource* and in the EC2 Instance option select your EC2 server \
    additional VPC security group (select DEFAULT)
8. Database Authentication: defaul Password authentication.