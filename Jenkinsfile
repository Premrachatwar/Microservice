pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker build -t premrachatwar/paymentservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') { 
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push premrachatwar/paymentservice:latest "
                    }
                }
            }
        }
    }
}
