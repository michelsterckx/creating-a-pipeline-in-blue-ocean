pipeline {
  agent {
    docker {
      image 'node:6-alpine'
    }

  }
  stages {
    stage('deploy on server 1') {
      steps {
        ansibleTower(towerServer: 'Ansible Tower', jobTemplate: 'Alfresco 5 - deploy', verbose: true)
      }
    }
    stage('deploy on server 2') {
      steps {
        ansibleTower(towerServer: 'Ansible Tower', jobTemplate: 'Alfresco 5 - deploy', inventory: 'demo2', verbose: true)
      }
    }
  }
}