pipeline {
    agent any

    environment {
        IMAGE = "your-dockerhub-username/myapp:latest"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'echo Build completed'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo Tests completed'
            }
        }

        stage('Code Quality') {
            steps {
                echo 'Running SonarQube scan...'
                sh 'echo "SonarQube scan"'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging application...'
                sh 'echo Package created'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running Trivy security scan...'
                sh 'docker run --rm aquasec/trivy image alpine:latest'
            }
        }
    }

    post {
        success {
            echo 'Pipeline SUCCESS ✅'
        }
        failure {
            echo 'Pipeline FAILED ❌'
        }
    }
}
