---
title: jenkins
date: 2018-09-26
categories: Tools
tags:
---
## Jenkins installation

### What is Jenkins?
Jenkins is a self-contained, open source automation server which can be used to automate all sorts of tasks related to building, testing, and delivering or deploying software.<br>

### Prerequisites
- `apache-tomcat-8.5.34`  
- `Jenkins.war`  
- `jdk1.8.0_144`





``` xml
# Step 1.  
# conf/server.xml, port: 919  
<Connector port="919" protocol="HTTP/1.1"
           connectionTimeout="20000"
           redirectPort="8443" />
           ```
``` bash
# Step 2.  
#  bin/catalina.sh
export PATH=$PATH:/usr/java/jdk1.8.0_144/bin  

# Step 3.  
# Download jenkins.war  
sudo wget  https://updates.jenkins-ci.org/download/war/2.143/jenkins.war  
unzip -oq jenkins.war -d jenkins  
sudo sh bin/catalina.sh start  

# password of jenkins administrator  
sudo cat  /root/.jenkins/secrets/initialAdminPassword  

```  
