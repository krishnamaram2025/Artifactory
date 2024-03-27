Project Title
============================

Jfrog Artifactory is used to store artifacts after build the source code


# Manual Jfrog Artifactory set up

Step 1: install java ans set environ ment variables

$yum install -y java-1.8.0-openjdk-devel

$echo "export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-1.el7_6.x86_64" >> /etc/profile

$./etc/profile or source /etc/profile

$env | grep JAVA

$yum install -y net-tools rsync

$wget https://api.bintray.com/content/jfrog/artifactory-rpms/jfrog-artifactory-oss/jfrog-artifactory-oss-$latest.rpm;bt_package=jfrog-artifactory-oss

$yum install -y jfrog-artifactory-oss-6.6.5.rpm

$echo "export ARTIFACTORY_HOME=/opt/jfrog/artifactory" >> /etc/profile

$./etc/profile or source /etc/profile

$env | grep ARTIFACTORY_HOME

$systemctl start artifactory.service

$systemctl enable artifactory.service

https://www.centlinux.com/2019/01/install-jfrog-artifactory-on-centos-rhel-7.html

https://www.theserverside.com/video/4-ways-to-upload-a-JAR-to-a-JFrog-Artifactory-repository#:~:text=1.,JAR%20onto%20the%20deployment%20screen.



# Automation Jfrog Artifactory set up

Installation 
==============================

$yum update -y && yum upgrade -y

$yum install git -y && yum install wget -y && yum install unzip -y && yum install curl -y

$yum install ansible -y

Set up
==============

Step 1: switch to root user

sudo su -l

passwd root

step 2: enable password authentication

vi /etc/ssh/sshd_config

PasswordAuthentication yes

permitroorlogin yes

systemctl restart sshd

step 3: generate ssh keys for key based authentication

ssh-keygen

ssh-copy-id root@localhost


Execution Flow
=======================
step 1: clone repo

$git clone https://github.com/krishnamaram2/Configuration_Manager.git

Step 2:

$cd Configuration_Manager/src

$ansible-playbook -i hosts artifactory.yml







Types of repositories in Artifactory
1.local 2.remote 3.virtual 4.distribution
How to integrate Artifactory to Jenkins
step 1  install artifactory plugin in Jenkins
Manage Jenkins=>manage plugins => 
step 2  add ertifactory server details in jenkins
manage jenkins=> configure system => artifactory=> add artifactory server
server id
url : https://34.7.1.28:8081/artifactory
username: admin
pwd: admin_123
step 3 to create Jenkins Job
New item=> create free style project=> general=> scm=> build triggers=> build environment
choose maven3-artifactory integration
artifactory configuration'
artifactory server: https://34.7.1.28:8081/artifactory
target release repository: <target repo>
=> Build
choose Invoke artifactory maven3
select goal
package

if you get any error as below 
This build step needs to know where your Maven3 is installed. Please do so from

Then go to Global tool configuration => choose Maven
