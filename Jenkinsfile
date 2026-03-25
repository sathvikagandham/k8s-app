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
                docker tag k8s-app:%BUILD_NUMBER% sathvika019/k8s-app:%BUILD_NUMBER%
docker push sathvika019/k8s-app:%BUILD_NUMBER%
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
