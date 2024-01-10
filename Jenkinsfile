pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
                sh 'git --version'
                sh 'whoami'
                sh 'git clone https://github.com/majesticteam23/nodedemo.git'  
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker docker buildx build -t majesticteam47/nodetest:latest /path/to/dockerfile_directory'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push majesticteam47/nodetest:latest'
            }
        }
    }
    post{
        always{
            sh 'docker logout'

        }
    }

}

