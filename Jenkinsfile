pipeline {
    agent {
        docker {
            image 'ubuntu'
            args '-u root'
        }
    }
    stages {
        stage('Enter Container') {
            steps {
                sh 'apt-get update && apt-get install -y git && apt-get install -y python3-pip'
                sh 'pip install awscli'
                sh 'echo "6" '
                sh 'aws configure set region us-east-1'
                sh 'aws cloudformation create-stack --stack-name S3-stack --template-body file://create.yaml --region "us-east-1"' 
            }
        }
    }
}
