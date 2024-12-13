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
                chmod u+x ./kubectl
                '''
            }
        }
        stage('Install Terraform') {
            steps {
                sh '''
                curl -LO "https://releases.hashicorp.com/terraform/1.10.2/terraform_1.10.2_linux_arm64"
                chmod +x terraform_1.10.2_linux_arm64
                '''
            }
        }
        stage('show get pods') {
            steps {
                withKubeConfig([credentialsId: "credentialsId", serverUrl: 'https://192.168.49.2:8443']) {
                    sh './kubectl get pods'
                }
            }
        }
        stage('show terraform version') {
            steps {
                sh './terraform_1.10.2_linux_arm64 -version'
            }
        }
    }
}
