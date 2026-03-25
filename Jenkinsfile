pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/sathvikagandham/k8s-app'
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

        stage('Push Docker Image') {
            steps {
                bat 'docker push sathvika19/k8s-app:%BUILD_NUMBER%'
            }
        }

    }
}
