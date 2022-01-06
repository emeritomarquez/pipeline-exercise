# pipeline-exercise

Working 05/01/2021

print_greetings
create_infrastructure
upload_file:
download_file:

notes on aws command to get IP of the ec2 instance

ubuntu@ip-172-31-4-250:~$ aws ec2 describe-instances --query 'Reservations[*].Instances[*].{Instance:InstanceId,Subnet:SubnetId}' --output text
i-088416d4e088f2928     subnet-c375abbb
i-084adfd084dfb544a     subnet-cbaa0296
i-0be1182edfa3392fc     subnet-cbaa0296
i-00e5b5d5a07e2dbf9     subnet-cbaa0296
i-025a4c17546780d17     subnet-cbaa0296
i-0dbb074221bdf2073     subnet-c375abbb


ubuntu@ip-172-31-4-250:~$ aws ec2 describe-instances --instance-ids i-088416d4e088f2928 | grep "PrivateIpAddress"
                    "PrivateIpAddress": "172.31.18.180",
                            "PrivateIpAddress": "172.31.18.180",
                            "PrivateIpAddresses": [
                                    "PrivateIpAddress": "172.31.18.180"

ubuntu@ip-172-31-4-250:~$ aws ec2 describe-instances --instance-ids i-088416d4e088f2928 | grep "PrivateIpAddress" | head -1
                    "PrivateIpAddress": "172.31.18.180",

ubuntu@ip-172-31-4-250:~/pipeline-exercise-part2$  aws ec2 describe-instances --query 'Reservations[*].Instances[*].PublicIpAddress' --output text
35.85.151.185
34.221.48.106
18.236.78.54
ubuntu@ip-172-31-4-250:~/pipeline-exercise-part2$ aws ec2 describe-instances --query 'Reservations[*].Instances[*].PublicIpAddress' --output text | tail -1
18.236.78.54

