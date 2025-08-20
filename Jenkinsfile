pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8s-Token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://257F24C1B229A2DEBF459EA3EE8D8F6C.gr7.ap-south-1.eks.amazonaws.com') {
                     sh "kubectl apply -f deployment-service.yml"
                   }
                }
            }
        
        stage('verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8s-Token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://257F24C1B229A2DEBF459EA3EE8D8F6C.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
            }
         }
      }
   }
}
