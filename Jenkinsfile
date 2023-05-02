pipeline {
	agent any
	environment {
	   SKIP_PREFLIGHT_CHECK=true
	   CI=false
	}

	stages {
	    stage('SCM Checkout') {
            steps {
                cleanWs()
                git branch: 'refector_Release/develop' , url: 'https://jenkinsdevstringx:JLvRu9eaT9NsH6v9gTML@bitbucket.org/devstringxtechnologies/fehrms.git'
                echo 'Fetching code'
            }

	    }

	    stage('Execute run shell') {
            steps{
                sh '''
               bash /var/lib/jenkins/run.sh
                '''
                echo 'Done'
            }
        } 
        //cp -r /var/lib/jenkins/workspace/node_modules/ /var/lib/jenkins/workspace/test/
        stage('Deploy'){
            steps{
            // cleanWs()    
             echo 'Build Successful'
        }
        }
	}
}
