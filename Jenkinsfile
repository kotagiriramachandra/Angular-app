pipeline {
	agent any
	parameters{
		string defaultValue: 'develop', description: 'Source Branch', name: 'BRANCH_NM'
	}
	stages {
		stage ('build') {
			steps {
				echo " Before build for branch: ${params.BRANCH_NM}"
        checkout scmGit(branches: [[name: "*/${params.BRANCH_NM}"]], extensions: [], userRemoteConfigs: [[credentialsId: 'git-cred', name: 'origin', url: 'https://github.com/kotagiriramachandra/Angular-app.git']])
				bat 'npm.cmd install'
				bat 'ng build -prod'        
        echo " After build for branch: ${params.BRANCH_NM}"
			}
		}
	}  
  post {
    always {
      echo 'Build process initiated and'
    }
    success {
      echo 'build process completed successfully'
    }
    failure {
      echo 'build process failed'
    }
  }
}
