pipeline {
    agent any

    stages {
        stage('Kubernetes_Deploy') {
            steps {
               withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'k8file', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: '') {
                        sh "kubectl create -f deployment-service.yml -n webapps"
                }
            }
        }
        stage('Kubernetes_GetInfo') {
            steps {
               withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'k8file', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: '') {
                        sh "kubectl get pods -n webapps"
                        sh "kubectl get svc -n webapps"
                }
            }
        }
    }
    post {
        success {
           archiveArtifacts artifacts: 'Jenkinsfile, Dockerfile, **/*.yml', 
           followSymlinks: false
        }
    }
}
