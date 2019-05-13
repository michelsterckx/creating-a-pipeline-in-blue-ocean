pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('error') {
      steps {
        ansibleTower(towerServer: 'pvxodevo1.ux.pv.be', jobTemplate: 'Alfresco 5 - deploy')
      }
    }
  }
}