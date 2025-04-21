pipeline {
    agent any

    environment {
        HTML_FILE = 'index.html'
        GIT_CREDENTIALS_ID = 'github-credentials' // Replace with your actual Jenkins credentials ID
        GIT_REPO_URL = 'https://github.com/sivaram66/Jenkins-Practice.git'
        GIT_BRANCH = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: "${env.GIT_BRANCH}", credentialsId: "${env.GIT_CREDENTIALS_ID}", url: "${env.GIT_REPO_URL}"
            }
        }

        stage('Create HTML File') {
            steps {
                script {
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
                    
                    // Write index.html to root
                    writeFile file: "${env.HTML_FILE}", text: htmlContent
                }
            }
        }

        stage('Commit & Push to GitHub') {
            steps {
                script {
                    sh '''
                        git config user.email "you@example.com"
                        git config user.name "Jenkins CI"
                        git add index.html
                        git commit -m "Auto-update index.html via Jenkins" || echo "No changes to commit"
                        git push origin ${GIT_BRANCH}
                    '''
                }
            }
        }
    }

    post {
        success {
            echo "Website deployed via GitHub Pages!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
