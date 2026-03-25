pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
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
                sh '''
                docker build -t k8s-app:${BUILD_NUMBER} .
                docker tag k8s-app:${BUILD_NUMBER} sathvikagandham/k8s-app:${BUILD_NUMBER}
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker push sathvikagandham/k8s-app:${BUILD_NUMBER}'
            }
        }

    
    }
}
