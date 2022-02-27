
# How to install Docker on Centos8/Rhel8            and then Run Mariadb service via docker/and then Create a database ,then create a table,create a evaluation sheet




##Prerequisites 

 -A user account with sudo privileges
  
  -The firewalld manager disabled

## Add Docker Repository Using DNF
Use DNF to add and enable the official Docker CE repository. Type the following command in your terminal window:

sudo dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo

sudo dnf repolist -v

## Install Docker CE on CentOS 8/Rhel8
An efficient solution is to allow your CentOS 8 system to install the version that meets the criteria best, using the --nobest command:

sudo dnf install docker-ce –nobest

##  Install containerd.io Package Manually
Another option for installing Docker on CenOS 8 is to install the containerd.io package manually, in advance. This workaround allows you to install the latest docker-ce version.
Use the following command:

sudo dnf install https://download.docker.com/linux/centos/7/x86_64/stable/Packages/containerd.io-1.2.10-3.2.el7.x86_64.rpm

Now we can proceed to install the latest version of docker-ce with a simple command:

sudo dnf install docker-ce -y

The output below confirms that docker-ce-3:19.03.5-3.el7.x86_64 has been successfully installed

## Start and Test Docker

Enable Docker

sudo systemctl enable --now docker

systemctl status docker

## Add User to Docker User Group
Add your user to the docker group with the following command:

sudo usermod -aG docker $USER

id $USER

## Disable firewalld on CentOS 8/Rhel8
As mentioned previously, we need to disable firewalld for DNS resolution inside Docker containers to work.
One simple command is enough to disable firewalld in CentOS 8/Rhel8:

sudo systemctl disable firewalld

## Testing Docker Installation by Pulling Test Container Image
Download a small alpine docker container image to test the installation

docker pull alpine

docker images



## Initiate Alpine Container Image
Use Docker to run the container with the downloaded image and try doing a simple apk update:
docker run -it --rm alpine /bin/sh

/# apk update

##  mariadb using docker container
docker search mariadb
 
 docker pull mariadb 
 
 docker images
## creating mariadb container
docker run --name mariadbLogical -e MYSQL_ROOT_PASSWORD=password -d mariadb

docker ps -a


## starting mariadb container

       docker restart mariadbLogical 
       docker start mariadbLogical 
       docker status mariadbLogical
       
## Connect mariadb container using below command.

docker exec -it mariadbLogical bash


## login to mariadb run following below command

mysql -u root -p Enter passward 


## Now Starting work with mariadb

MariaDB [manoj_sheets]> show databases;

+--------------------+

| Database           |

+--------------------+

| information_schema |

| manoj_sheets       |

| mysql              |

| performance_schema |

| sys                |

+--------------------
## Documentation Ended



