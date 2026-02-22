pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-rahamrrr', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://F4F8CD62BB6EE5568C6641A5E78A536B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-rahamrrr', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://F4F8CD62BB6EE5568C6641A5E78A536B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
