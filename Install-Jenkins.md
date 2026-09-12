### Install Jenkins

# sudo apt install -y fontconfig openjdk-21-jre
# java -version

### Add Jenkins LTS repository:

# mkdir -p /etc/apt/keyrings
# wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key

### Add repository:
# echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | \
sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

### Install Jenkins:
# apt update
# apt install -y jenkins

### Start Jenkins
# systemctl enable jenkins
# systemctl start jenkins

# http://YOUR_SERVER_IP:8080

### Get initial Jenkins password
# cat /var/lib/jenkins/secrets/initialAdminPassword

> Install suggested plugins

### Install git and apache2
# apt install git apache2

# usermod -aG www-data jenkins

# ps aux | grep jenkins

### check and add 
# which rsync
# visudo or vi /etc/sudoers
 jenkins ALL=(ALL) NOPASSWD: /usr/bin/rsync
# rsync

### Create pipe line 
Jenkins Dashboard > New Item > project name > Pipeline > OK

### Configure Pipeline from Git
Select project > Configure > pipeline > Pipeline script from SCM > Git > 

### auto deploy
select project > configuration > Triggers > GitHub hook trigger for GITScm polling > save

on GitHub > repo > Setting > Webhooks > playbook url > http://44.201.32.2:8080/github-webhook/ > Content type: application/json >
Just the push event > Active: ✓ > 