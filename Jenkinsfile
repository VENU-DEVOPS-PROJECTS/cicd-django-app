pipeline {
    agent any
    environment {
        dockerhub=credentials('docker-venuchanapathi1998')
    }
    stages{
        stage('Code'){
            steps{
                git url: 'https://github.com/VENU-DEVOPS-PROJECTS/cicd-django-app.git', branch: 'main' 
            }
        }
        stage('Build and Test'){
            steps{
                sh 'docker build . -t venuchanapathi1998/node-todo-test:latest'
            }
        }
        stage('Push'){
            steps{
        	     sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
                 sh 'docker push venuchanapathi1998/node-todo-test:latest'
            }
        }
        stage('Deploy'){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
