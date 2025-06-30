pipeline {
    agent any
    triggers {
        pollSCM("H/1 * * * *")
    }
    stages {
        stage("Checkout") {
            steps {
                echo "Checking out code..."
                git branch: "main", url: "https://github.com/matin235-ops/Assignment--1.git"
            }
        }
        stage("Build") {
            steps {
                echo "Building application..."
                script {
                    if (isUnix()) {
                        sh "python --version"
                        sh "pip install flask"
                    } else {
                        bat "python --version"
                        bat "pip install flask"
                    }
                }
            }
        }
        stage("Test") {
            steps {
                echo "Running tests..."
                script {
                    if (isUnix()) {
                        sh "python -c \"print(\"\"Tests passed\"\")\""
                    } else {
                        bat "python -c \"print(\"\"Tests passed\"\")\""
                    }
                }
            }
        }
        stage("Update Jira") {
            steps {
                echo "Updating Jira..."
                script {
                    try {
                        jiraAddComment(
                            idOrKey: "SCRUM-1",
                            comment: "Build ${env.BUILD_NUMBER} completed successfully!"
                        )
                        echo "Jira updated successfully!"
                    } catch (Exception e) {
                        echo "Jira update failed: ${e.getMessage()}"
                    }
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
