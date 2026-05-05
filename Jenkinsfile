pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                // Jenkins will automatically pull from SCM (GitHub)
                echo 'Checking out code from GitHub...'
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

        stage('Package') {
            steps {
                echo 'Packaging application...'
                sh 'echo Package created'
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
