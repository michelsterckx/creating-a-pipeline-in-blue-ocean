pipeline {
  agent {
    docker {
      image 'node:6-alpine'
    }

  }
  stages {
    stage('error') {
      steps {
        echo 'Hoi!'
      }
    }
    stage('somein') {
      steps {
        sh 'ping www.gva.be'
      }
    }
  }
}