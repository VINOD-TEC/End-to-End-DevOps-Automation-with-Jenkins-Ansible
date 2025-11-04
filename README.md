# End-to-End DevOps Automation with Jenkins + Ansible
# Objective: Automate infrastructure setup and app deployment using IaC.
Tools & Technologies: Jenkins, Ansible, Docker, Git, Linux
Deliverables:
  1. Jenkins pipeline integrated with Ansible
  2. Playbook for app deployment
  3. Continuous delivery demo

# Architecutre Diagram

<img width="1128" height="467" alt="image" src="https://github.com/user-attachments/assets/5952db27-1bf3-4b00-a30d-186dd7e1d6b3" />


🚀 Quick Start
  1.  Deploy Two EC2 Instances (Ubuntu) one for Jenkins, Docker, and Ansible.
  2.  One for Production Server

Instances:
  1. t2.medium for jenkins, docker, Ansible.
  2. t2.micro for Prod server

<img width="1916" height="364" alt="image" src="https://github.com/user-attachments/assets/6aa8a9ae-b323-41b4-92bb-345d6a40b048" />

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

# After the Installation is done start and enable the services
    systemctl start docker
    systemctl start Jenkins
    systemctl start ansible
    systemctl enable docker
    systemctl enable jenkins
 
# Install Ansible
   	sudo apt update
 	  sudo apt install software-properties-common
 	  sudo add-apt-repository --yes --update ppa:ansible/ansible
 	  sudo apt install ansible -y

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

<img width="1651" height="909" alt="image" src="https://github.com/user-attachments/assets/16a1fae8-fe9c-484f-94d3-bbafad2f0370" />

# Install plugins in jenkins maven and ansible
<img width="1914" height="599" alt="image" src="https://github.com/user-attachments/assets/ad5a36bc-d6fc-4f5e-b3da-fa12b78fa8b5" />

# Install maven and ansible in Jenkins
<img width="1702" height="568" alt="image" src="https://github.com/user-attachments/assets/73bd0efe-2315-4cee-af6e-e916a233fd6e" />

<img width="1592" height="552" alt="image" src="https://github.com/user-attachments/assets/a31eb774-dc3e-441d-9a7d-003bf6114ad3" />

# Create a Job and write a pipeline
<img width="1886" height="834" alt="image" src="https://github.com/user-attachments/assets/3abd062f-30cb-4f5e-bcd0-0cd6bbf4c8a1" />

# Setting up webhooks
    Click on settings on github repo

<img width="1408" height="680" alt="image" src="https://github.com/user-attachments/assets/b08c64f0-61c5-48e3-ab41-80a811dd5207" />

    Select Webhook and add webhook
    
  <img width="1232" height="763" alt="image" src="https://github.com/user-attachments/assets/d4a2e72f-5b91-4c5f-a124-ac3cace582af" />

  <img width="864" height="199" alt="image" src="https://github.com/user-attachments/assets/3cce5b84-53fe-496f-afd4-8828ae2e0cd1" />

  # Create a Ansible Playbook and Inventory file in the github repo
      deploy-docker.yml
      dev.inv

  # 🔁 Setup GitHub Webhook
    Go to your GitHub repository Settings → Webhooks
    Add a new webhook pointing to your Jenkins URL
  
  # 🔄 CI/CD Flow
    Once a commit is pushed to GitHub:
      The webhook triggers Jenkins
      Jenkins builds the app with Maven
      Docker image is built and pushed to DockerHub
      Ansible deploys the container to the production server

# ✅ Output
# 🖥️ Application Running on Production Server
  <img width="1316" height="200" alt="image" src="https://github.com/user-attachments/assets/dfee3eb2-3c49-4996-b284-44191d983d9a" />

  # Docker images

  <img width="1242" height="205" alt="image" src="https://github.com/user-attachments/assets/833ec15b-6ed7-4089-8e88-3eb844952994" />

# DockerHub Upload
  <img width="1907" height="497" alt="image" src="https://github.com/user-attachments/assets/600cccec-704a-4893-ac8c-359c0d97e0ca" />
  
# 🎯 Summary

    This project demonstrates a complete CI/CD pipeline using Jenkins, Docker, and Ansible — enabling automated build, deployment, 
    and delivery with minimal manual intervention.

# Author: [Irshed Ahmed S]
    GitHub: [https://github.com/irshadahmed03/End-to-End-DevOps-Automation-with-Jenkins-Ansible.git]
