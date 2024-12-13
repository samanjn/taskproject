pipeline {
    agent any
    environment {
        CREDENTIALSID = credentials('credentialsId') // Credential ID for Secret File
    }
    stages {
        stage('show get pods') {
            withKubeConfig([credentialsId: "${CREDENTIALSID}" , serverUrl: 'https://127.0.0.1:51455']) {
            sh 'kubectl get pods'
            }
        }
    }
}