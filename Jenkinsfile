pipeline {
    agent any
    // environment {
    //     CREDENTIALSID = credentials('credentialsId') // Credential ID for Secret File
    // }
    stages {
        stage('Install kubectl') {
            steps {
                sh '''
                curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
                chmod +x ./kubectl
                '''
            }
        }
        stage('Show get pods') {
            steps {
                withKubeConfig([credentialsId: "${CREDENTIALSID}", serverUrl: 'https://192.168.49.2:8443']) {
                    sh './kubectl get pods'
                }
            }
        }
        stage('Show Terraform version') {
            steps {
                sh 'terraform -version'
            }
        }
    }
}