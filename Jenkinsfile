pipeline {
    agent {
        docker {
            image 'ubuntu'
            args '-u root'
        }
    environment {
        AWS_ACCESS_KEY_ID = credentials('AKIAWQ2ANG2GS4J7Y5XW')
        AWS_SECRET_ACCESS_KEY = credentials('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')
        AWS_REGION = 'us-east-1'
        STACK_NAME = 'my-stack'
    }
    stages {


        stage('Delete stack') {
            steps {
		    sh 'apt-get update && apt-get install -y git && apt-get install -y python3-pip'
                sh 'pip install awscli'
                withAWS(region: AWS_REGION, credentials: 'aws-credentials') {
                    sh "aws cloudformation delete-stack --stack-name ${STACK_NAME}"
                }
            }
        }
    }
    post {
        always {
            withAWS(region: AWS_REGION, credentials: 'aws-credentials') {
                def stackExists = sh(script: "aws cloudformation describe-stacks --stack-name ${STACK_NAME} 2>/dev/null | grep -q 'StackName' && echo 'true' || echo 'false'", returnStdout: true).trim() == 'true'
                if (stackExists) {
                    error "Stack deletion failed. Stack ${STACK_NAME} still exists."
                }
            }
        }
    }
}
