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
            export AWS_ACCESS_KEY_ID=${TF_AK}
            export AWS_SECRET_ACCESS_KEY=${TF_SK}
            export AWS_DEFAULT_REGION="eu-west-2"
            cat README.md
          """
         }
      }
    } 

    stage('Run user script') {
      steps {
         withCredentials ([usernamePassword(credentialsId: 'LM-SVC-TF-CREDS', usernameVariable: 'TF_AK', passwordVariable: 'TF_SK')
        ]) {
          sh """
	        export PATH=$PATH:"/usr/local/bin":"/.local/bin":
            export AWS_ACCESS_KEY_ID=${TF_AK}
            export AWS_SECRET_ACCESS_KEY=${TF_SK}
            export AWS_DEFAULT_REGION="eu-west-2"
            chmod +x user_creation.sh
            sh ./user_creation.sh
          """
      }
      }
    }
  }
}
