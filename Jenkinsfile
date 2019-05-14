
/* version 1.0 */
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
                importTowerLogs: true,
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
                importTowerLogs: true,
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
        ansibleTower(towerServer: 'Ansible Tower', jobTemplate: 'Alfresco 5 - deploy', inventory: 'devo2',  verbose: true)
      }
    }
    stage('deploy on server 2') {
      steps {
        ansibleTower(towerServer: 'Ansible Tower', jobTemplate: 'Alfresco 5 - deploy', inventory: 'devo3', verbose: true)
      }
    }
    
    
     stage('restart alfresco servers') {
     
        parallel {
           stage('restart alfresco 1') {
              steps {
                 
                ansibleTower(towerServer: 'Ansible Tower', 
              jobTemplate: 'Service Control - install', 
                importTowerLogs: true,
                inventory: 'devo2',
                extraVars: '''---
service_state: "restarted"
service_name:  "alfresco"''', 
                verbose: true)
                     
                
              }
           }
          
          
           stage('restart alfresco 2') {
              steps {
              
              ansibleTower(towerServer: 'Ansible Tower', 
              jobTemplate: 'Service Control - install', 
                importTowerLogs: true,
                inventory: 'devo3',
                extraVars: '''---
service_state: "restarted"
service_name:  "alfresco"''', 
                verbose: true)
                     
                
              }
           }
          
          
        }
    
    }
    
  }
}
