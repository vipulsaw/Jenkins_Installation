# Jenkins_Installation

Installing Jenkins on Ubuntu 24.04
Here's a step-by-step guide to install Jenkins on Ubuntu 24.04:

Prerequisites
Ubuntu 24.04 system

sudo privileges

Java (Jenkins requires Java 11 or 17)

Installation Steps
1. Update System Packages
bash
```
sudo apt update && sudo apt upgrade -y
```
2. Install Java (OpenJDK 17 recommended)
bash
```
sudo apt install -y openjdk-17-jdk
```
Verify installation:

bash
```
java -version
```
3. Add Jenkins Repository and Key
bash
```
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
```
4. Install Jenkins
bash
```
sudo apt update
sudo apt install -y jenkins
```
5. Start and Enable Jenkins Service
bash
```
sudo systemctl enable jenkins
sudo systemctl start jenkins
```
Check status:

bash
```
sudo systemctl status jenkins
```
6. Open Firewall (if enabled)
bash
```
sudo ufw allow 8080
sudo ufw allow OpenSSH
sudo ufw enable
```
7. Access Jenkins Web Interface
Open your browser and go to: http://your_server_ip:8080

Retrieve the initial admin password:

bash
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
Follow the setup wizard to complete installation



Create your first admin user

Configure Jenkins as needed

Optional: Change Jenkins Port (if 8080 is in use)
Edit the config file:

bash
sudo nano /etc/default/jenkins
Change HTTP_PORT=8080 to your desired port, then restart Jenkins:

bash
```
sudo systemctl restart jenkins
```
That's it! You now have Jenkins installed on Ubuntu 24.04.

## Post-Installation

### Install suggested plugins during setup

Pipeline

Docker Pipeline

Git

SSH Agent

Credentials Binding

Kubernetes CLI

Helm
