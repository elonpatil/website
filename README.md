# Jenkins CI/CD Project with Ansible, Jenkins and K8s
![image](https://github.com/elonpatil/website/assets/134854789/c054973b-6a0f-4cc4-b434-0370fb759801)

## Step 1: First, launched an EC2 instance manually with name 'Main'.
### Main: Java, Jenkins
![image](https://github.com/elonpatil/website/assets/134854789/880f752f-5b5e-4d8d-9dd1-63e3505afefa)

## Step 2: Installed the Terraform and runt the script to lunch 3 more instances.
![image](https://github.com/elonpatil/website/assets/134854789/4fcd47ac-3747-4bc8-a1de-1af5fe027052)
![image](https://github.com/elonpatil/website/assets/134854789/285643d1-b2d2-4db5-9815-69bae03d6281)

## Step 3: For the required configuration, install Ansible and write playbook and run it from Main instance.
### On Machine3: Java, Docker, Kubernetes
### On Machine1: Docker, Kubernetes
### On Machine2: Docker, Kubernetes
![image](https://github.com/elonpatil/website/assets/134854789/b181d8f8-2d39-449d-8a0a-875a76d5f33d)
![image](https://github.com/elonpatil/website/assets/134854789/f2721199-fdee-442d-97c3-148ac13dd26a)

## Step 4: Configured the jenkins and added the Machine 3 as the K8s-Master Node
![image](https://github.com/elonpatil/website/assets/134854789/acd17067-9be4-4bff-a498-b409472b6e8e)
##       Write the pipeline script so that Git commit triggers the pipeline to clone the Github repo --> build and push image to DockerHub --> Create the Deployment and SVC on K8s.  
```
    pipeline {
    agent none
    environment {
        DOCKERHUB_CREDENTIALS=credentials'ccf6c018-30d4-4632-a809-e6f7bda5a25a'
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Git') {
            agent {
               label 'K8s Master'
            }
            steps {
                git 'https://github.com/elonpatil/website.git'
            }	
        }
        stage('Docker') {
            agent {
               label 'k8s-master'
            }
            steps {
                sh 'sudo docker build /home/ubuntu/jenkins/workspace/testpipeline -t elonpatil/project2'
                sh 'sudo echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'sudo docker push elonpatil/project2'
            }
        }
	stage('K8s') {
            agent {
               label 'K8s-Master'
            }
            steps {
                sh 'kubectl apply -f deployment.yaml'
		sh 'kubectl apply -f service.yaml'
            }
        }
    }
```
## Result: 
![image](https://github.com/elonpatil/website/assets/134854789/453950a3-abcf-4c75-9bef-f286cd56f9db)
![image](https://github.com/elonpatil/website/assets/134854789/ca4f8edc-0fad-4fb0-911f-7bcd310e8602)

## After GIt-Hub Commit: 
![image](https://github.com/elonpatil/website/assets/134854789/4ceaca19-3b26-4df5-b1b8-0f4614c1d66f)
![image](https://github.com/elonpatil/website/assets/134854789/00cf5000-4859-4c5f-9e02-3a7a73eda93b)
![image](https://github.com/elonpatil/website/assets/134854789/e73b8591-527a-4740-bbc0-00058f58cd02)
![image](https://github.com/elonpatil/website/assets/134854789/77887996-b09b-45b2-9210-e7e5a3d07612)
![image](https://github.com/elonpatil/website/assets/134854789/3f154f64-f6e0-4158-9477-6e18118a0691)
