# DevOps_GL_Hometask: Jenkins/-CI pipelines/Groovy

### I performed this task as follows:
- Installed Jenkins, which is located on AWS VM
- I attached a Jenkins slave to it, which is also located on the AWS virtual machine
- Took my old camping website project that we will deploy to a web server in the cloud
- Added a webhook trigger to the Jenkins job
- Created two branches in the repository
- Configured Ansible to configure two servers (test and main)
- Created a telegram bot that will notify about completed pipelines

<hr>

### How to install? 

- | [Jenkins](https://pkg.jenkins.io/debian-stable/) | 
- | [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) | 
- | [Git](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-20-04) | 
- | [Webhook Triger](https://plugins.jenkins.io/generic-webhook-trigger/) |

<hr>

## Jenkins Sign In

![image](https://user-images.githubusercontent.com/55669434/214715916-87c76f89-7d0f-40f6-b2d5-3def9d500fd7.png)

## Jobs

![image](https://user-images.githubusercontent.com/55669434/214716184-65dc85ce-0600-42c9-b93f-c536c79d9090.png)

![image](https://user-images.githubusercontent.com/55669434/214716292-e83fe94a-fdf8-4856-86df-23d361b26ccd.png)

## Pipelines

### For main branch

![image](https://user-images.githubusercontent.com/55669434/214716599-2d957610-8ec5-4788-9e4f-c9bc1ab71b49.png)

### For feature branch

![image](https://user-images.githubusercontent.com/55669434/214716788-9d0aae83-0ca0-4fc1-92a4-484c51b6976e.png)

## Credentials

![image](https://user-images.githubusercontent.com/55669434/214716962-004d3a17-02cb-42d6-81ec-958999547a69.png)

## Telegram Bot Messages

![image](https://user-images.githubusercontent.com/55669434/214717165-8b5d4850-c789-4f09-a233-72141783cacd.png)
![image](https://user-images.githubusercontent.com/55669434/214717221-6c404445-a526-4d82-b2c8-d7a06aafdb84.png)

## Website

![image](https://user-images.githubusercontent.com/55669434/214717961-9a242aa4-103d-4349-9863-d694c09649bd.png)

<hr>

The principle of operation of this multibranch pipeline is that when we change something in the feature branch, 
an ansible playbook script is launched, which deploys it on a test server for testing the website. 
And when there is a push to the main branch, then the website must be launched on the main web server
