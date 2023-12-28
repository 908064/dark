pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('praveen300420')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
                sh 'git --version'
                sh 'whoami'
                sh 'git clone https://github.com/majesticteam23/nodedemo.git'

           j
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t praveen300420/nodedemo:${1} .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $Dark@007 | docker login -u $praveen300420 --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push praveen300420/nodedemo:${1}'
            }
        }
}

}

