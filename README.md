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

## Step 5: 

## Step 6: 

## Step 7: 




