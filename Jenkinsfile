node {
  checkout scm
}

pipeline {
  agent any
 

  stages {
    stage('Create Environment') {
      steps {
        {
          sh """
	        rm trufflehog || true
          docker run gesellix/trufflehog --json https://github.com/andrewclacko > trufflehog
          cat trufflehog 
          """
         }
      }
    } 
  }
}
