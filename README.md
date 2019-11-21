# Install RStudio Server on an Amazon-AWS instance

## Prerequisites

First of all create a VPC, a subnet and an internet gateway to connect the VPC to the internet. Then add the internet gateway created to the route table. One route table for one subnet.

## Installing

Create an new EC2 instance in Amazon AWS the AMI Amazon Linux 2 is free tier eligible.

Enable auto-assign Public IP let to attribute an public IP for our instance we just created.

We then create a security group in which we should open the port 8787 (the one associated with Rstudio Server).

The connection to our instance can be managed with some tools like Putty or directly in the command prompt via SSH. Using Putty we should enter the public IP associated to our instance and the key in .ppk format.

### Install R 3.4 and Rstudio Server 1.2.5019 the OS associated with our instance is CentOS 6.

```Sudo yum update -y
Sudo amazon-linux-extras install R3.4
wget https://download2.rstudio.org/server/centos6/x86_64/rstudio-server-rhel-1.2.5019-x86_64.rpm
sudo yum install rstudio-server-rhel-1.2.5019-x86_64.rpm
```

### Create an "RStudio Server account" :
```Sudo useradd user
Echo user:password | sudo chpasswd```

We can also launch in our instance the code to install RStudio Server in batch mode :
```#!/bin/bash
sudo yum update -y
sudo amazon-linux-extras install R3.4 -y
wget https://download2.rstudio.org/server/centos6/x86_64/rstudio-server-rhel-1.2.5019-x86_64.rpm
sudo yum -y install rstudio-server-rhel-1.2.5019-x86_64.rpm
sudo useradd fcmdr
echo fcmdr:12345 | sudo chpasswd```

