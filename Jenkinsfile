pipeline {
    agent any
    environment {
        KUBECONFIG_FILE = credentials('kubeconfig-id') // Credential ID for Secret File
    }
    stages {
        stage('Deploy') {
            steps {
                sh """
                export KUBECONFIG=\$KUBECONFIG_FILE
                kubectl get pods
                """
            }
        }
    }
}
