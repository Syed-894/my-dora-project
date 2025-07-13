pipeline {
    agent any
    environment {
        GIT_COMMIT = sh(script: 'git rev-parse HEAD', returnStdout: true).trim()
    }
    stages {
        stage('Build') {
            steps {
                echo "Building..."
                echo "COMMIT_HASH: ${env.GIT_COMMIT}"
            }
        }
        stage('Test') {
            steps {
                sh 'pip install -r requirements.txt'
                sh 'pytest'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    if (Math.random() < 0.2) {
                        error "Deployment failed"
                    } else {
                        echo "Deployment succeeded"
                    }
                }
            }
        }
    }
}
