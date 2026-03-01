pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                stage('Checkout') {
    steps {
        git 'https://github.com/zuber383/capstone-project-1.git'
    }
}
            }
        }

        stage('Build Image') {
            steps {
                bat 'docker build -t bookmyshow-app .'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'docker run bookmyshow-app pytest'
            }
        }

        stage('Deploy App') {
            steps {
                bat 'docker run -d -p 8081:80 bookmyshow-app'
            }
        }
    }

    post {
        always {
            bat 'docker ps -aq | xargs docker rm -f'
        }
    }
}
