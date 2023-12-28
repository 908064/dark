pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('praveen300420')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/majesticteam23/nodedemo.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t praveen300420/nodedemo:1 .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push praveen300420/nodedemo:1'
            }
        }
}
post {
       
    }
}

