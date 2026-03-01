pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/bookmyshow-ci-cd.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t bookmyshow-app .'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'docker run bookmyshow-app pytest'
            }
        }

        stage('Deploy App') {
            steps {
                sh 'docker run -d -p 8081:80 bookmyshow-app'
            }
        }
    }

    post {
        always {
            sh 'docker ps -aq | xargs docker rm -f'
        }
    }
}
