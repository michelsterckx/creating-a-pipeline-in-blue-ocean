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
        sh 'node --version'
        pwd()
        ansibleTower(towerServer: 'pvx0devo1.ux.pv.be', jobTemplate: 'Alfresco 5 - deploy', credential: 'admin', verbose: true)
      }
    }
  }
}