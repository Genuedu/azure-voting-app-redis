pipeline {
   agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage('Docker build') {
         agent {
            docker { 
               image 'node:14-alpine' 
               }
         }
         steps {
            sh('docker images -a')
            sh( """
               cd azure-vote/
               docker images -a
               docker build -t jenkins-pipeline .
               docker images -a
               cd ..
            """)
         }
      }
   }
}
