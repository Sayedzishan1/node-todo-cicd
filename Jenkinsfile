pipeline {
    agent any

    environment {
        RECIPIENTS = 'sayed.zishan@neosoftmail.com'  // Define the recipients for email notifications
    }

    stages {
        stage('Clone') {
            steps {
                echo "Cloning the repository"
                git 'https://github.com/Sayedzishan1/node-todo-cicd.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building the Docker image"
                sh 'docker build -t todo-app .'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the Todo app"
                sh 'docker-compose down'
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        success {
            // Send success email when the build is successful
            mail to: "$RECIPIENTS",
                 subject: "Build Success: ${env.JOB_NAME} ${env.BUILD_NUMBER}",
                 body: "The build was successful!\n\nJob: ${env.JOB_NAME}\nBuild Number: ${env.BUILD_NUMBER}\nBuild URL: ${env.BUILD_URL}"
        }
        failure {
            // Send failure email when the build fails
            mail to: "$RECIPIENTS",
                 subject: "Build Failed: ${env.JOB_NAME} ${env.BUILD_NUMBER}",
                 body: "The build has failed.\n\nJob: ${env.JOB_NAME}\nBuild Number: ${env.BUILD_NUMBER}\nBuild URL: ${env.BUILD_URL}"
        }
    }
}
