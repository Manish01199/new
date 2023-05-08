pipeline {
  agent {
    docker { image 'ubuntu' }
  }
  stages {
    stage('Install Dependencies') {
      steps {
        sh 'apt-get update && apt-get install -y awscli'
      }
    }
    stage('Create Stack') {
      steps {
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIAWQ2ANG2GS4J7Y5XW', secretKeyVariable: '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']]) {
          sh 'aws cloudformation create-stack --stack-name my-stack --template-body file://create.yml'
        }
      }
    }
  }
}
