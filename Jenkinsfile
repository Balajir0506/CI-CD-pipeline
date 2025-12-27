pipeline {
    agent any

    tools {
        maven 'maven3'
        jdk 'jdk17'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-creds',
                    url: 'https://github.com/Balajir0506/CI-CD-pipeline.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t demo-app:1.0 .'
            }
        }

        stage('Docker Run') {
            steps {
                sh '''
                docker rm -f demo-container || true
                docker run -d --name demo-container demo-app:1.0
                '''
            }
        }
    }
}


