pipeline {
    agent any

    stages {
        stage('Deploy_To_Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://F21096648B59B437D00CEED6F34B6E8D.gr7.us-east-1.eks.amazonaws.com']]) {
                        sh "kubectl create -f deployment-service.yml"
                        sh "kubectl get svc -n webapps"
                }
          }
      }
  }

}
