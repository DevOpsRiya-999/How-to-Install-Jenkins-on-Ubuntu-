# How-to-Install-Jenkins-on-Ubuntu-
jenkins installation on ubuntu 

Jenkins installers are available for several Linux distributions.

Debian/Ubuntu

Prerequisites
Minimum hardware requirements:

256 MB of RAM

1 GB of drive space (although 10 GB is a recommended minimum if running Jenkins as a Docker container)

Recommended hardware configuration for a small team:

4 GB+ of RAM

50 GB+ of drive space
==========================================
step1: 
# Installation of Java
>>sudo apt update
>>sudo apt install fontconfig openjdk-21-jre
>>java -version
# step2: install jenkins 
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
# step3:
>>sudo systemctl enable jenkins
>>sudo systemctl start jenkins
>>sudo systemctl status jenkins
step4:
Unlocking Jenkins
>>Browse to http://localhost:8080 (or whichever port you configured for Jenkins when installing it) and wait until the Unlock Jenkins page appears.
>>
![Uploading image.png…]()

# How to install jenkins using docker

>>docker pull jenkins/jenkins:lts
>>docker run -d -p 8080:8080 -p 50000:50000 --name jenkins-master -v jenkins-data:/var/jenkins_home jenkins/jenkins:lts

-d: Runs the container in the background.
-p 8080:8080: Maps port 8080 on the host machine to port 8080 in the container (the default Jenkins web UI port).
-p 50000:50000: Maps port 50000 for Jenkins agents to communicate with the controller.
--name jenkins-master: Assigns a name to your container for easy reference.
-v jenkins-data:/var/jenkins_home: Maps the container's /var/jenkins_home directory to a Docker volume named jenkins-data on your host. 


