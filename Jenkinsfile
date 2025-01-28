pipeline {
    agent none // This means that the pipeline will not run on any agent by default

    stages {
        stage('Clone') {
            agent { label 'agent' } // This stage will run on an agent with the label 'agent'
            steps {
                echo "Cloning the repository"
                git 'https://github.com/ajitfawade/node-todo-cicd.git' // Cloning the GitHub repository
            }
        }

        stage('Build') {
            agent { label 'agent' } // Run the build stage on an agent with the label 'agent'
            steps {
                echo "Building the Docker image"
                sh 'docker build -t todo-app .' // Building the Docker image
            }
        }

        stage('Deploy') {
            agent { label 'agent' } // Run the deploy stage on an agent with the label 'agent'
            steps {
                echo "Deploying the Todo app"
                sh 'docker-compose down'  // Bringing down existing services
                sh 'docker-compose up -d' // Bringing services up in detached mode
            }
        }
    }
}
