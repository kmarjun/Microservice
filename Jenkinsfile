pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                 withKubeConfig(caCertificate: '', clusterName: 'shopping', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://139.185.54.24:6443') {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                 withKubeConfig(caCertificate: '', clusterName: 'shopping', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://139.185.54.24:6443') {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
