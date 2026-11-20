jenkins :
pipeline {
    agent any

    tools {
        maven 'MAVEN-HOME'
    }

    stages {
        stage('git repo & clean') {
            steps {
                bat "if exist OLTRS rmdir /s /q OLTRS"
                bat "git clone https://github.com/archanareddyse/OLTRS"
                bat "mvn clean -f OLTRS"
            }
        }

        stage('install') {
            steps {
                bat "mvn install -f OLTRS"
            }
        }

        stage('test') {
            steps {
                bat "mvn test -f OLTRS"
            }
        }

        stage('package') {
            steps {
                bat "mvn package -f OLTRS"
            }
        }
    }
}




AWS:
sudo apt update
sudo apt install docker.io->yes
sudo apt install nano
sudo apt install git
git clone (repo url)
ls
cd (file in ls)
ls
nano Dockerfile
(FROM tomcat:9-jdk11
COPY **/*.war /usr/local/tomcat/webapps/)(ctrl X->yes)
sudo docker build -t app
sudo docker images
sudo docker run -d --name new -p 8080:8080 app

ipv4 address
cd target
ls
ipv4 target


minikube:
minikube start
kubectl create deployment xyz --image=nginx
kubectl expose deployment xyz --image=nginx
kubectl expose deployment xyz --type=NodePort --port=80 --target-port=80
kubectl get deployments
kubectl get pods
kubectl scale deployment xyz --replicas=4
kubectl port-forward svc/xyz 8090:80 
minikube dashboard
