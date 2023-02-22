## Jenkins-Ansible-Apache Tomcat
## Image
![ansible-1](https://user-images.githubusercontent.com/111736742/220746641-259b683e-84d4-49db-90d7-964c61aa90ea.jpg)

## Ansible-Installation
```bash
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
yum install epel-release-latest-7.noarch.rpm
yum update -y
yum install git python python-devel python-pip openssl ansible -y
ansible --version
```
![ansible-1server](https://user-images.githubusercontent.com/111736742/220700977-12fd2b7d-0761-428c-bce3-15a07abe17b0.png)

## Ansible-Node Configuration
```bash
cd /etc/ansible
sudo vi hosts
--------------------
#And Place This content
[TomcatServers]
#node-1
172.31.42.33
#node-2
172.31.34.221
#node-3
172.31.38.224
#node-4
172.31.35.200
----------------------
```
![ansible-2-node](https://user-images.githubusercontent.com/111736742/220701143-27305434-f8f4-456c-9785-747bcd145251.png)
## To check connectvity between ansible-master & nodes
![ansible-ping](https://user-images.githubusercontent.com/111736742/220707106-fb8979ff-bb1e-46ad-9e5c-0289020f0bb3.png)
## copy this [1.context.xml  2.tomcat-users.xml  3.tomcat.yaml]  content into ansible home directory.

#which is there in github-repository.
![ansible-copy-content](https://user-images.githubusercontent.com/111736742/220710173-b34ffe15-d10c-4fcd-80b7-8f2b27a39538.png)

## SonarQube Download & Installation
```bash
cd /opt
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.9.10.61524.zip
unzip sonarqube-8.9.10.61524.zip
mv sonarqube-8.9.10.61524 sonarqube
useradd chaitu
passwd chaitu
chown -R chaitu:chaitu sonarqube
cd /opt/sonarqube/bin/linux-x86-64
vi sonar.sh 
--------------
edit this
#RUN_AS_USER=
RUN_AS_USER=chaitu
su - chaitu
[And start SonarQube]
cd /opt/sonarqube/bin/linux-x86-64
sh sonar.sh start
sh sonar.sh status
ip:9000
```

## Nexus Download & Installation
```bash
yum install java-1.8* -y
cd /opt
wget https://download.sonatype.com/nexus/3/nexus-3.47.1-01-unix.tar.gz
tar -xvzf  nexus-3.47.1-01-unix.tar.gz
mv nexus-3.47.1-01 nexus
useradd chaitu
passwd chaitu
chown -R chaitu:chaitu nexus
chown -R chaitu:chaitu sonatype-work
cd /opt/nexus/bin
vi nexus.rc
--------edit---------
#run_as_user="chaitu"
----------edit--------
sh nexus start
sh nexus status
ip:8081
```
## Before-changes


