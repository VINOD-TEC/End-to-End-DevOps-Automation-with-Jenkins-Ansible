pipeline {
    agent any

    tools {
        // Install the Maven version configured as "mymaven" and add it to the PATH
        maven "mymaven"
    }

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/irshadahmed03/End-to-End-DevOps-Automation-with-Jenkins-Ansible.git'
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build . -t shiakahmed53/appansible:latest'
            }
        }

        stage('DockerHub Push') {
            steps {
                withCredentials([string(credentialsId: 'docker-hub', variable: 'DockerHubPwd')]) {
                    sh 'docker login -u shiakahmed53 -p $DockerHubPwd'
                }
                sh 'docker push shiakahmed53/appansible:latest'
            }
        }

        stage('Docker Deploy') {
            steps {
                ansiblePlaybook(
                    credentialsId: 'Prod-Server',
                    disableHostKeyChecking: true,
                    installation: 'ansible',
                    inventory: 'dev.inv',
                    playbook: 'deploy-docker.yml',
                    vaultTmpPath: ''
                )
            }
        }
    }
}
