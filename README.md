# Ansible-AutoScaling

Ansible Playbook to create Autoscaling group, Load balancer and website/application from Git. 

## Description:

This Ansible Playbook can be used to create AWS [Auto Scaling Group](https://docs.aws.amazon.com/autoscaling/ec2/userguide/AutoScalingGroup.html), [Load Balancer](https://aws.amazon.com/elasticloadbalancing/?whats-new-cards-elb.sort-by=item.additionalFields.postDateTime&whats-new-cards-elb.sort-order=desc), [Key Pair](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html) and [Security Group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html) and create desired number of EC2 instances with autoscaling group for the GIT website or application.   

## Features

- This Playbook is uses [Dynamic Inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_dynamic_inventory.html) for managing the instances created by Autoscaling.
- We can manage the playbook easily using the variables file and Vars_prompt which will ask for desired key name, desired security group name and instance type.
- The playbook checks for chanages in Git files and update the EC2 instances one by one. The Ec2 updation process is done using second play and it uses Serial key word to run the updation one by one. This ensures that the website/application is always up and running even during updation process.  

## Major Ansible Modules Used

1. ec2_key
2. ec2_group
3. ec2_elb_lb
4. ec2_lc
5. ec2_asg
6. ec2_instance_info
7. add_host
8. git
9. pause
10. file

## Variables from file

The variables used in this playbook are given below. You can edit these variables from file autoscaling_vars.yml ,
```
region: "Desired region name"                                   #Eg: ap-south-1
zone1: "Desired zone name"                                      #Eg: ap-south-1a
zone2: "Desired zone name"                                      #Eg: ap-south-1b
ami: "Desired AMI"                                              #Eg: ami-010aff33ed5991201
access_key: "your IAM access key"
secret_key: "your IAM secret key"            
git_url: "Git hub URL for the desired application/website"   
health_time: 25                                 
asg_min: 2
asg_max: 2
asg_desired: 2
```

## How to use?

```
yum install git unzip -y
git clone https://github.com/MarkAntonyGit/Ansible-AutoScaling.git
cd Ansible-AutoScaling
vim autoscaling_vars.yml  <<--------- make necessary changes
ansible-playbook playbook_ansible_autoscaling.yml
``` 

### Sample Screenshots

-- Play 

![](https://i.ibb.co/KrmhwxM/asg1.jpg)
![](https://i.ibb.co/P9JW7WX/asg2.jpg)

-- Sample Website Updation

![](https://i.ibb.co/N6ZcTRg/asg3.jpg)
![](https://i.ibb.co/WvJ5zch/asg4.jpg)

-------- Mark Antony ------------------------------------------------------------------------------------------------------------------------------- linkedin.com/in/mark-antony-345473211 ------------------------------------------------------------------------------------------------------- markantony.alenchery@gmail.com ----------------------------------------------------
