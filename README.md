# End-to-End DevOps Automation with Jenkins + Ansible
# Objective: Automate infrastructure setup and app deployment using IaC.
Tools & Technologies: Jenkins, Ansible, Docker, Git, Linux
Deliverables:
  1. Jenkins pipeline integrated with Ansible
  2. Playbook for app deployment
  3. Continuous delivery demo

🚀 Quick Start
  1.  Deploy Two EC2 Instances (Ubuntu) one for Jenkins, Docker, and Ansible.
  2.  One for Production Server

Instances:
  1. t2.medium for jenkins, docker, Ansible.
  2. t2.micro for Prod server

# Install Jenkins
   	sudo apt update
    sudo apt install fontconfig openjdk-21-jre
    sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
    https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
    echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
    https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null
    sudo apt update -y
    sudo apt install jenkins -y

# Install Docker
 	# Add Docker's official GPG key:
 	sudo apt-get update
 	sudo apt-get install ca-certificates curl
 	sudo install -m 0755 -d /etc/apt/keyrings
 	sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
 	sudo chmod a+r /etc/apt/keyrings/docker.asc
 	# Add the repository to Apt sources:
 	echo \
 	"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
 	$(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
 	sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
 	sudo apt-get update -y
 	sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

# Install Ansible
   	sudo apt update
 	  sudo apt install software-properties-common
 	  sudo add-apt-repository --yes --update ppa:ansible/ansible
 	  sudo apt install ansible -y

<img width="1916" height="364" alt="image" src="https://github.com/user-attachments/assets/6aa8a9ae-b323-41b4-92bb-345d6a40b048" />

<img width="1829" height="649" alt="image" src="https://github.com/user-attachments/assets/8debc089-1718-41cc-8f5f-53d10e39cae0" />

# Give permissions for docker and Jenkins
    sudo usermod -aG docker ubuntu
    sudo usermod -aG docker jenkins
    newgrp docker
    sudo getent group docker

# Set jenkins password
<img width="1813" height="942" alt="image" src="https://github.com/user-attachments/assets/f561a9de-4938-41db-b86c-798ff083b892" />

<img width="1293" height="163" alt="image" src="https://github.com/user-attachments/assets/08fb5102-78f2-4771-acc5-6e438cb81754" />

# copy the password and paste in jenkins



  
  





