//Pipeline with GIT integration

pipeline {
    agent any
 
      options {
    timeout(time: 30, unit: 'MINUTES')
}

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

       stage('Stop Old Container') {
           steps {
        sh 'docker rm -f nice_khorana || true'
           }
       }

     stage('Run Container') {
           steps {
        sh 'docker run -d -p 8082:80 --name nice_khorana docker-jenkins-app2'
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
