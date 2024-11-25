pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5DA8FFE65F8C20A95E3024BBC428019D.yl4.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
            stage('verify deployment') {
            steps {
              withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5DA8FFE65F8C20A95E3024BBC428019D.yl4.eu-north-1.eks.amazonaws.com']]) {
                   sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

