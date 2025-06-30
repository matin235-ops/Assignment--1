pipeline {
    agent any

    triggers {
        pollSCM('H/1 * * * *') // Poll every minute
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/matin235-ops/Assignment--1.git'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building Flask application...'
                // Add build steps here if needed
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running unit tests...'
                // Add unit tests here
            }
        }
        
        stage('Performance Testing') {
            steps {
                echo 'Running JMeter performance tests...'
                script {
                    // Start the Flask application in background
                    sh 'nohup python app.py &'
                    sleep 10 // Wait for app to start
                    
                    // Run JMeter tests
                    sh 'jmeter -n -t performance-testing/flask-app-test.jmx -l performance_results.jtl'
                    
                    // Stop the Flask application
                    sh 'pkill -f "python app.py"'
                }
            }
            post {
                always {
                    // Archive performance test results
                    archiveArtifacts artifacts: 'performance_results.jtl', fingerprint: true
                    // Publish performance test results
                    publishTestResults testResultsPattern: 'performance_results.jtl'
                }
            }
        }
        
        stage('Docker Build & Push') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credential') {
                        def app = docker.build("matinkhaled23/assignment1-app")
                        app.push("latest")
                        app.push("${env.BUILD_NUMBER}")
                    }
                }
            }
        }
        
        stage('Update Jira') {
            steps {
                echo 'Updating Jira issue...'
                script {
                    try {
                        // Add comment to Jira issue (replace SCRUM-1 with your actual issue key)
                        jiraAddComment(
                            idOrKey: "SCRUM-1", 
                            comment: "Build ${env.BUILD_NUMBER} completed successfully! Docker image pushed to matinkhaled23/assignment1-app:${env.BUILD_NUMBER}"
                        )
                        echo 'Jira issue updated successfully!'
                    } catch (Exception e) {
                        echo "Failed to update Jira: ${e.getMessage()}"
                        // Don't fail the build if Jira update fails
                    }
                }
            }
        }
    }
    
    post {
        always {
            // Clean workspace
            cleanWs()
        }
        success {
            echo 'Pipeline completed successfully!'
            // Add notification logic here
        }
        failure {
            echo 'Pipeline failed!'
            // Add failure notification logic here
        }
    }
}
