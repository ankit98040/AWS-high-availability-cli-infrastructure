# AWS-high-availability-cli-infrastructure

Link to article: https://pramanik-85849.medium.com/high-availability-infrastructure-setup-on-aws-using-aws-cli-46a488bc3833

CLI Commands to create high availability infrastructure

AWS EC2, S3, EBS, Cloudfront

aws ec2 run-instances --image-id ami-0a9d27a9f4f5c0efc --count 1 --instance-type t2.micro --key-name lastkey --security-group-ids sg-06ec206128d0a8695 --subnet-id subnet-b2167dfe

aws ec2 create-volume --availability-zone ap-south-1b --size 2 --volume-type gp2

aws ec2 create-tags --resources vol-0bfe39f4bb82c0452 --tags  Key=Name,Value=NewDrive

fdisk -l
fdisk /dev/xvdb

aws s3api create-bucket --bucket ha-bucket98040 --create-bucket-configuration LocationConstraint=ap-south-1 --acl public-read

aws s3 cp ha.png s3://ha-bucket98040/ha.png  --acl public-read

aws cloudfront create-distribution  --origin-domain-name ha-bucket98040.s3.amazonaws.com --default-root-object ha.png
