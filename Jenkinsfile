pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/mishranidhi2305/two-tier-flask-app.git', credentialsId: 'git-creds'
            }
        }

        stage('Build') {
            steps {
                echo "Building Flask app..."
                sh "echo Simulate build here"
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh "echo Simulate tests here"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                sh "echo Simulate deployment here"
            }
        }
    }
}
