pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://46C3C1F70F165B6F9F964970EF0AC389.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://46C3C1F70F165B6F9F964970EF0AC389.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
