# Name: Matin Khalid 
# qiu21235
# CI/CD Pipeline Project

This project demonstrates a CI/CD pipeline using Jenkins, GitHub, and Docker. The pipeline automatically detects changes pushed to a GitHub repository, triggers a Jenkins job to build and test the application, and generates and pushes a Docker image to Docker Hub.

## Files
- `app.py`: A simple Python application.
- `Dockerfile`: Configuration for containerizing the application.
- `Jenkinsfile`: CI/CD pipeline configuration.

## Steps to Run
1. Set up Jenkins with the required plugins.
2. Configure Docker Hub credentials in Jenkins.
3. Push this repository to GitHub.
4. Trigger the Jenkins pipeline.

## Docker Hub
The Docker image will be pushed to the Docker Hub account `matinkhaled23`.
