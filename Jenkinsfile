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
        ansibleTower(towerServer: 'Ansible Tower', jobTemplate: 'Alfresco 5 - deploy', verbose: true, jobType: 'job')
      }
    }
  }
}