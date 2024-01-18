pipeline {
    agent any 

    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker23')
    }

    stages {
        stage('SCM Checkout') {
            steps {
                sh 'rm -rf nodedemo || true'  // Remove existing directory if it exists
                sh 'git clonehttps://github.com/908064/dark.git '
                echo 'test1'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'test2'
                sh 'docker build -t majesticteam47/nodedemo:latest .'
            }
        }

        stage('Login to DockerHub') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'docker23', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
                        sh "docker login -u $DOCKERHUB_USERNAME -p $DOCKERHUB_PASSWORD"
                    }
                    echo 'test3'
                }
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push kannan313/nodedemo:latest'
            }
        }
    }

    post {
        always {
            sh 'docker logout'
        }
    }
}
