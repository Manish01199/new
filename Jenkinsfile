pipeline {
  agent {
    docker {
            image 'ubuntu'
            args '-u root'
        }
  }
  stages {
    stage('Install Dependencies') {
      steps {
        sh 'apt-get update && apt-get install -y git && apt-get install -y python3-pip'
        sh 'pip install awscli'
      }
    }
    stage('Create Stack') {
      steps {
          sh 'aws configure set aws_access_key_id AKIAWQ2ANG2GS4J7Y5XW'
          sh 'aws configure set aws_secret_access_key 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'
          sh 'aws configure set region us-east-1'
          sh 'aws cloudformation create-stack --stack-name my-stack --template-body file://create.yml'
        
      }
    }
  }
}
