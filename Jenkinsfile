pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat """
                docker build -t k8s-app:%BUILD_NUMBER% .
                docker tag k8s-app:%BUILD_NUMBER% sathvikagandham/k8s-app:%BUILD_NUMBER%
                """
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker push sathvikagandham/k8s-app:%BUILD_NUMBER%'
            }
        }

    }
}
