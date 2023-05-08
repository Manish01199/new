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
        withCredentials([[accessKeyVariable: 'AKIAWQ2ANG2GS4J7Y5XW', secretKeyVariable: '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']]) {
          sh 'aws cloudformation create-stack --stack-name my-stack --template-body file://create.yml'
        }
      }
    }
  }
}
