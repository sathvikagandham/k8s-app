pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "sathvika019/k8s-app"
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
                docker tag k8s-app:%BUILD_NUMBER% sathvika019/k8s-app:%BUILD_NUMBER%
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                bat '''
                docker push sathvika019/k8s-app:%BUILD_NUMBER%
                '''
            }
        }

    }

    post {
        success {
            echo 'Build Successful 🎉'
        }

        failure {
            echo 'Build Failed ❌'
        }
    }
}
