pipeline {
    agent any

    environment {
        IMAGE = "your-dockerhub-username/myapp:latest"
    }

    stages {

        stage('Checkout') {
            steps {
                echo '🔹 Checking out code from GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo '🔹 Building application...'
                sh 'echo "Build completed"'
            }
        }

        stage('Test') {
            steps {
                echo '🔹 Running tests...'
                sh 'echo "Tests completed"'
            }
        }

        stage('Code Quality (SonarQube Placeholder)') {
            steps {
                echo '🔹 Running Code Quality Check...'
                sh 'echo "SonarQube scan placeholder"'
            }
        }

        stage('Docker Build') {
            steps {
                echo '🔹 Building Docker image...'
                sh 'docker build -t $IMAGE .'
            }
        }

        stage('Security Scan (Trivy)') {
            steps {
                echo '🔹 Running Trivy security scan...'
                sh 'docker run --rm aquasec/trivy image $IMAGE'
            }
        }

        stage('Docker Push') {
            steps {
                echo '🔹 Pushing image to DockerHub...'
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh '''
                        echo $PASS | docker login -u $USER --password-stdin
                        docker push $IMAGE
                    '''
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo '🔹 Deploying to Kubernetes...'
                sh '''
                    kubectl apply -f deployment.yaml
                    kubectl apply -f service.yaml
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline SUCCESS - Deployment completed'
        }
        failure {
            echo '❌ Pipeline FAILED - Check logs'
        }
    }
}
