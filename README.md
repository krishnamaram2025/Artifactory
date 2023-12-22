# Title
This project is intended to set up Artifactory server

# Phase 1: Create Artifactory server in AWS

    https://github.com/devops2023q2/terraform

# Phase 2: Install and configure software packages for Artifactroy

# Automation 
* Step 1: Run playbook
https://github.com/devops2023q2/ansible


# Create Repository
http://<<PUBLIC_IP>>:8081
Creating Repository login to artifactory server => Administration => repositories => add repositories => Local repository => Select package type : Generic => repository key : myrepo => Save and Finish

# Upload and Download files from Artifactory repos
* Upload
Application => Artifactory => Artifacts => Click on repo => click on Deploy => click on select file => Deploy
* Download
Application => Artifactory => Artifacts => Click on repo => click on | just side to 3 dots  => click on Download 

* Upload Artifacts using curl utility
syntax
curl -X PUT -u <USERNAME>:<PASSWORD> -T <source_file> <base_url>/<artifacory_repo>/artifactrname
ex
curl -X PUT -u user:passwd -T kri http://ip:8082/artifactory/krip/k

* Download artifacts from artifactory repo using curl utility
syntax
curl -sSf -u <USERNAME>:<PASSWORD> -O <base_url>/<artifacory_repo>/artifactrname
ex
curl -sSf -u user:passwd  http://ip:8082/artifactory/krip/k

# Manual steps
* Step 1: step1: Login to EC2 Intance i.e “artifactory”
```
sudo yum install -y net-tools rsync wget
```
 * Step 2 : install artifactory 
```
sudo yum install -y java-1.8.0-openjdk-devel 
sudo su 
echo "export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-1.el7_6.x86_64" >> /etc/profile 
source /etc/profile 
env | grep JAVA 
sudo wget https://releases.jfrog.io/artifactory/artifactory-rpms/artifactory-rpms.repo -O jfrog-artifactory-rpms.repo 
sudo mv jfrog-artifactory-rpms.repo /etc/yum.repos.d/ 
sudo yum update -y && sudo yum install jfrog-artifactory-oss -y 
sudo echo "export ARTIFACTORY_HOME=/opt/jfrog/artifactory" >> /etc/profile 
source /etc/profile 
env | grep ARTIFACTORY_HOME
sudo systemctl start artifactory.service 
systemctl enable artifactory.service
```

* Step 3: testing
```
http://<<PUBLIC_IP>>:8081/artifactory
```
