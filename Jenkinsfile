node {
  checkout scm
}

pipeline {
  agent any
 
  stages {
    stage('Create Environment') {
      steps {
         withCredentials ([usernamePassword(credentialsId: 'LM-SVC-TF-CREDS', usernameVariable: 'TF_AK', passwordVariable: 'TF_SK')
      ]) {
          sh """
	        export PATH=$PATH:"/usr/local/bin":"/.local/bin":
          rm trufflehog || true
          docker run gesellix/trufflehog --json https://github.com/andrewclacko > trufflehog
          cat trufflehog 
          """
         }
      }
    } 
  }
}



