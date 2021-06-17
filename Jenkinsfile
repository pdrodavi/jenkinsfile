pipeline {
  agent any
  
  stages {
  
    stage('Select branch') {
      steps {
        script {
          BRANCH= input message: 'Your Branch'
        }
      }
    }
        
    stage('Cloning Git') {
      steps {
        git branch: BRANCH, url: 'https://github.com/pdrodavi/pipeline-node.git'
      }
    }
        
    stage('Install dependencies') {
      steps {
        echo "Install"
      }
    }
     
    stage('Test') {
      steps {
         echo "Test"
      }
    }      
  }
}
