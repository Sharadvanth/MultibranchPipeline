pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker build -t sharadvanth/checkoutservice:${BUILD_NUMBER} ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push sharadvanth/checkoutservice:${BUILD_NUMBER} "
                    }
                }
            }
        }
    }
    post {
        success {
           archiveArtifacts artifacts: 'Jenkinsfile, Dockerfile, **/*.tar', 
           followSymlinks: false
        }
    }
}
