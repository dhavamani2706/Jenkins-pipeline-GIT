//Pipeline with GIT integration

pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                echo "Code already cloned from Git"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t docker-jenkins-app2 .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8081:80 docker-jenkins-app2'
            }
        }
    }

    post {
        success {
            echo "Docker deployment successful"
        }
        failure {
            echo "Deployment failed"
        }
    }
}
