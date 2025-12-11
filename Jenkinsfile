pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "flask-app-demo:latest"
    }

    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/mishranidhi2305/two-tier-flask-app.git', credentialsId: 'git-creds'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image from cloned repo
                    sh "docker build -t $DOCKER_IMAGE ."
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Stop and remove any existing container
                    sh "docker rm -f flask-app || true"
                    // Run container
                    sh "docker run -d --name flask-app -p 5000:5000 $DOCKER_IMAGE"
                }
            }
        }

        stage('Test') {
            steps {
                sh "curl -f http://localhost:5000 || echo 'App not responding yet'"
            }
        }
    }
}
