pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }

        stage('Security Scan') {
            steps {
                sh 'docker run --rm aquasec/trivy image alpine:latest'
            }
        }

        stage('Code Quality') {
            steps {
                echo 'SonarQube scan (simulated)'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging application...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline SUCCESS ✔'
        }
        failure {
            echo 'Pipeline FAILED ❌'
        }
    }
}
