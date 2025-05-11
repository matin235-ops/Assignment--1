pipeline {
    agent any

    triggers {
        pollSCM('H/1 * * * *') // Poll every minute
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/matin235-ops/Assignment--1.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Docker Build & Push') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credential') {
                        def app = docker.build("matinkhaled23/assignment1-app")
                        app.push("latest")
                    }
                }
            }
        }
    }
}
