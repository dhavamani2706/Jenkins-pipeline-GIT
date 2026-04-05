#Pipeline with GIT integration

pipeline {
    agent any
      parameters {
          string(name: 'NAME', defaultValue: 'Dhavamani', description: 'Enter Name')
      }
      environment {
          App_Name = 'Test App'
          ENV_Name = 'QA'
      }
     stages {
         stage ('Build') {
             steps {
           echo "Building the application...."
        }
     }    
     stage ('Test') {
         steps {
         echo "App name: ${App_Name}"
       }
     }
     stage ('user input') {
         steps {
         echo "Enter name: ${params.NAME}"
       }
     }
     stage ('Deploy') {
         steps {
         echo "Deployed the application in the ${ENV_Name} environment"
       }  
     }
   }
     post {
         success {
             echo "successfully build the application"
         }
         failure {
             echo "Build failed"
         }
         always {
             echo "Execution completed successfully..!!!"
         }
     }
  }
