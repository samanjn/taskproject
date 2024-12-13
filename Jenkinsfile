pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Checkout the repository
                git branch: 'main', url: 'https://github.com/samanjn/taskproject.git'
            }
        }
        
        stage('Echo File Content') {
            steps {
                // Print the content of a specific file
                sh 'echo testfile'
            }
        }
    }
}
