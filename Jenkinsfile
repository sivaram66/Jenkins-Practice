pipeline {
    agent any

    environment {
        HTML_FILE = 'index.html'
        TARGET_DIR = 'web'
    }

    stages {
        stage('Checkout') {
            steps {
                // Get latest code from GitHub
                git branch: 'main', url: 'https://github.com/sivaram66/Jenkins-Practice.git'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Simulate deployment by copying to a folder
                    sh "mkdir -p ${env.TARGET_DIR}"
                    sh "cp ${env.HTML_FILE} ${env.TARGET_DIR}/"

                    echo "Deployed updated HTML file to ${env.TARGET_DIR}/${env.HTML_FILE}"
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline completed and deployed successfully!"
        }
        failure {
            echo "Pipeline failed."
        }
    }
}
