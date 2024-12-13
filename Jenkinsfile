pipeline {
    agent any
    environment {
        KUBECONFIG_FILE = credentials('kubeconfig-id') // Credential ID for Secret File
    }
    stages {
        stage('Install kubectl') {
            steps {
                sh '''
                curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
                chmod +x ./kubectl
                mv ./kubectl /usr/local/bin/kubectl
                '''
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                export KUBECONFIG=$KUBECONFIG_FILE
                kubectl get pods
                '''
            }
        }
    }
}