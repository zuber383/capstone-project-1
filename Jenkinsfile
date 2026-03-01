pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t capstone-app .'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'docker run --rm capstone-app'
            }
        }

        stage('Deploy Application') {
            steps {
                bat 'docker run -d -p 8081:80 capstone-app'
            }
        }
    }

    post {
        always {
            bat 'docker ps -aq | docker rm -f'
        }
    }
}
