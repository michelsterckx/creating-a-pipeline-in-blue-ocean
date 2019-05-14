pipeline {
  agent {
    docker {
      image 'node:6-alpine'
    }

  }
  stages {
    
  
    stage('stop alfresco servers') {
     
        parallel {
           stage('stop alfresco 1') {
              steps {
                 
                ansibleTower(towerServer: 'Ansible Tower', 
              jobTemplate: 'Service Control - install', 
                inventory: 'devo2',
                extraVars: '''---
service_state: "stopped"
service_name:  "alfresco"''', 
                verbose: true)
                     
                
              }
           }
          
          
           stage('stop alfresco 2') {
              steps {
              
              ansibleTower(towerServer: 'Ansible Tower', 
              jobTemplate: 'Service Control - install', 
                inventory: 'devo3',
                extraVars: '''---
service_state: "stopped"
service_name:  "alfresco"''', 
                verbose: true)
                     
                
              }
           }
          
          
        }
    
    }
    
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
