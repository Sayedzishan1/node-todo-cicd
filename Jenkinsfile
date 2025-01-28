pipeline {
    agent new // Use any available agent

        stage('Clone') {
            steps {
                echo "Cloning the repository"
                git 'https://github.com/Sayedzishan1/node-todo-cicd.git' // Using Jenkins' git step
            }
        }

        stage('Build') {
            steps {
                echo "Building the Docker image"
                sh 'docker build -t todo-app .' // Building the Docker image
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the Todo app"
                sh 'docker-compose down'   // Bringing down any existing services
                sh 'docker-compose up -d'  // Bringing the services up in detached mode
            }
        }
    
}
