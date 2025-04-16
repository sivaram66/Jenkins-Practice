pipeline {
    agent any
    
    environment {
        HTML_FILE = 'index.html' // Name of the HTML file
        TARGET_DIR = 'web' // Directory to deploy the HTML
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from the repository
                git 'https://github.com/sivaram66/Jenkins-Practice.git' // Replace with your repository URL
            }
        }
        
        stage('Create HTML File') {
            steps {
                script {
                    // Create the HTML content
                    def htmlContent = '''<!DOCTYPE html>
                    <html lang="en">
                    <head>
                        <meta charset="UTF-8">
                        <meta name="viewport" content="width=device-width, initial-scale=1.0">
                        <title>Hello Message</title>
                    </head>
                    <body>
                        <h1>Hello, How are you?</h1>
                    </body>
                    </html>'''

                    // Write the HTML content to a file
                    writeFile file: "${env.TARGET_DIR}/${env.HTML_FILE}", text: htmlContent
                }
            }
        }

        stage('Deploy') {
            steps {
                // Display success message and location of the file
                echo "HTML file created at ${env.TARGET_DIR}/${env.HTML_FILE}"
                // You can add deployment steps here, such as copying the file to a web server
            }
        }
    }
    
    post {
        success {
            echo "Pipeline completed successfully."
        }
        failure {
            echo "Pipeline failed."
        }
    }
}
