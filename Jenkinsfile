pipeline {
    agent any
    environment {
        KUBECONFIG_FILE = credentials('kubeconfig-id') // Credential ID for Secret File
        CLIENT_CRT = credentials('client-crt') // Credential ID for client.crt
        CLIENT_KEY = credentials('client-key') // Credential ID for client.key
        CA_CRT = credentials('ca-crt') // Credential ID for ca.crt
    }
    stages {
        stage('Install kubectl') {
            steps {
                sh '''
                curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
                chmod +x ./kubectl
                '''
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                export KUBECONFIG=$KUBECONFIG_FILE
                mkdir -p ~/.kube
                cp $CLIENT_CRT ${env.WORKSPACE}/.kube/client.crt
                cp $CLIENT_KEY ${env.WORKSPACE}/.kube/client.key
                cp $CA_CRT ${env.WORKSPACE}/.kube/ca.crt
                ./kubectl get pods
                '''
            }
        }
    }
}