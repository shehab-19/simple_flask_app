pipeline {
    agent any

    stages {
        // Build Stage
        stage('Build') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
                        def customImage = docker.build("shehab19/flask-app:v1")
                        customImage.push()
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
                input message: 'Approve Deployment?', ok: 'Deploy'
                script {
                    // Run Flask App container (port 5555 on host, 5000 inside container)
                    docker.run('shehab19/flask-app:v1', '-p 5555:5000 --name flaskapp')
                }
            }
        }
    }
}
