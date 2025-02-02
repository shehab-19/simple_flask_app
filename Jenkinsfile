pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                        docker.withRegistry('https://index.dockerhub.io/v1/', 'dockerhub_credentials') {
                        def customImage = docker.build("flaskapp:0.0.1")
                        customImage.push()
                     }
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
