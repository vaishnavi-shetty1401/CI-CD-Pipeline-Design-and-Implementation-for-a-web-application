pipeline {
    agent any

    environment {
        IMAGE = "1401vaish/myapp"
    }

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/vaishnavi-shetty1401/CI-CD-Pipeline-Design-and-Implementation-for-a-web-application.git'
            }
        }

        stage('Install') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %IMAGE% .'
            }
        }

        stage('Push Image') {
            steps {
                bat 'docker push %IMAGE%'
            }
        }
    }
}
