pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
               script{
                docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
                def customImage = docker.build("shehab19/flask-app:v1")
                customImage.push()
               }
               }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add your test steps here
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add your deploy steps here
            }
        }
    }
}