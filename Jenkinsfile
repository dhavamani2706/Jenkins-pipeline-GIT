//Pipeline with GIT integration

pipeline {
    agent any
 
      options {
    timeout(time: 30, unit: 'MINUTES')
}
    environment {
       Port_no = "8081"
    }

    stages {

        stage('Clone Code') {
            steps {
                echo "Code already cloned from Git"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t docker-jenkins-app2:${BUILD_NUMBER} .'
            }
        }
      // stage ('Build Info') {
         //  steps {
        //     echo "Build Number: ${Build_Number}"
       //      }
      //  }

       stage('Stop Old Container') {
           steps {
        sh 'docker rm -f nice_khorana || true'
           }
       }

     stage('Run Container') {
           steps {
        sh 'docker run -d -p ${Port_no}:80 --name nice_khorana docker-jenkins-app2'
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
