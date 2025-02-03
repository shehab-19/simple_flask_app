pipeline {
    agent any

    stages {
        // Build Stage
        stage('Build') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {   // Use the Docker Hub credentials
                        def customImage = docker.build("shehab19/flask-app:v1")        // Build the Docker image
                        customImage.push()                                            // Push the Docker image to Docker Hub
                    }
                }
            }
        }

        // Testing Stage
        stage('Testing') {
            steps {
                script {
                    // Run the Ubuntu container for testing
                    docker.image('ubuntu:latest').inside {
                        sh 'echo "Testing inside Ubuntu container"'
                    }
                }
            }
        }

        // Deploy Stage with Input
        stage('Deploy') {
            steps {
                input message: 'Approve Deployment?', ok: 'Deploy'      // Input to approve the deployment
                script {
                    // Use the Docker block to run the container securely
                    docker.image('shehab19/flask-app:v1').run('-p 5555:5000 --name flaskapp')
                }
            }
        }
    }
}
