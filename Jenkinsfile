pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "sathvika19/k8s-app"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/sathvikagandham/k8s-app'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat '''
                docker build -t k8s-app:%BUILD_NUMBER% .
                docker tag k8s-app:%BUILD_NUMBER% sathvika19/k8s-app:%BUILD_NUMBER%
                '''
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub',
                usernameVariable: 'USER',
                passwordVariable: 'PASS')]) {

                    bat 'docker login -u %USER% -p %PASS%'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker push sathvika19/k8s-app:%BUILD_NUMBER%'
            }
        }

    }
}
