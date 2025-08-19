pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8s-Token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://072AA084582C165B3D835BF4B41DAAC9.yl4.ap-south-1.eks.amazonaws.com') {
                     sh "kubectl apply -f deployment-service.yml"
                   }
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'K8s-Token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://072AA084582C165B3D835BF4B41DAAC9.yl4.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
