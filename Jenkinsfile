pipeline {
    agent new // This means that the pipeline will not run on any agent by default
    stages {
        stage('Clone') {
            steps {
                echo "cloning the repository"
                git clone 'https://github.com/Sayedzishan1/node-todo-cicd.git' // This will clone the GitHub repository to the agent's workspace
            }
        }
        stage('Build') {
            echo "Building the image"
            steps {
                sh 'docker build -t todo-app .'
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying todo app"
                sh 'docker-compose down'
                sh 'docker-compose up -d'
            }
        }
    }
}
