pipeline {
    agent any
    // environment {
    //     CREDENTIALSID = credentials('credentialsId') // Credential ID for Secret File
    // }
    stages {
        stage('Install kubectl') {
            steps {
                sh '''
                curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/arm64/kubectl"
                chmod +x ./kubectl
                '''
            }
        }
        stage('Install Terraform') {
            steps {
                sh '''
                curl -LO "https://releases.hashicorp.com/terraform/1.10.2/terraform_1.10.2_linux_arm64.zip"
                unzip terraform_1.10.2_linux_arm64.zip
                chmod +x terraform
                mv terraform /usr/local/bin/
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