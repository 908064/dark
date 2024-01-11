pipeline {
    agent any 

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }

    stages {
        stage('SCM Checkout') {
            steps {
                sh 'rm -rf nodedemo || true'  // Remove existing directory if it exists
                sh 'git clone https://github.com/majesticteam23/nodedemo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                
                sh 'sudo docker build -t majesticteam47/nodedemo:latest'
            }
        }

        stage('Login to DockerHub') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
                        sh "docker login -u $DOCKERHUB_USERNAME -p $DOCKERHUB_PASSWORD"
                    }
                }
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push majesticteam47/nodedemo:latest'
            }
        }
    }

    post {
        always {
            sh 'docker logout'
        }
    }
}
