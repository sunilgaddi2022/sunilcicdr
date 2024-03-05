# Flask Application CI/CD Pipeline

This repository contains a Jenkins pipeline for automating the testing and deployment of a Flask application.

## Setup

1. Install Jenkins and configure with Python and necessary libraries.
2. Fork and clone this repository.
3. Configure the Jenkins pipeline to trigger on code changes.
4. Set up email notifications in Jenkins for build results.

## Jenkins Pipeline

The Jenkins pipeline defined in the Jenkinsfile performs the following stages:
- Build: Installs dependencies using pip.
- Test: Runs unit tests using pytest.
- Deploy: Deploys the application using Fabric.

## Triggers

The pipeline is triggered automatically on code changes pushed to the main branch of the repository.

## Notifications

Email notifications are sent for build success and failure.


