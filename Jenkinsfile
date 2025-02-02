pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    def customImage = docker.build("flaskapp:0.0.1")
                }
            }
        }
        
        stage("Test"){
            steps {
                echo "Testing.."
            }
        }
        
        stage("Deploy"){
            steps {
                echo "Deploying.."
            }
        }
    }
}
