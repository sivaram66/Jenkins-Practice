pipeline {
    agent any

    environment {
        // Define environment variables
        MY_VAR = 'Hello, Jenkins!'
        WORK_DIR = '/home/jenkins/workspace'
    }

    stages {
        stage('Clone Code') {
            steps {
                // Cloning code from GitHub repository
                git 'https://github.com/sivaram66/Jenkins-Practice.git'
            }
        }

        stage('Run Shell Script') {
            steps {
                // Running a simple shell script
                sh '''
                echo "This is a shell script"
                # Any other commands you want to run
                echo "Creating a new file"
                touch newfile.txt
                echo "This is a new file created by the shell script." > newfile.txt
                '''
            }
        }

        stage('Print Working Directory Content') {
            steps {
                // Printing the content of the current working directory
                sh 'ls -l'
            }
        }

        stage('Print Environment Variables') {
            steps {
                // Print environment variables
                echo "Environment Variable MY_VAR: ${MY_VAR}"
                echo "Working Directory: ${WORK_DIR}"
            }
        }
    }

    post {
        always {
            // Always run this after the pipeline finishes
            echo 'Pipeline execution completed.'
        }
    }
}
