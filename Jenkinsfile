pipeline {
  agent none // agent can only be overwritten if the initial value is 'none'
  stages {

    stage('Checkout') {
      agent any
      steps {
        script {
          echo 'This stage is blocking the executor because of the "agent any"'
        }
      }
    }

    stage('Choose Branch') {
      agent none
      steps {
        timeout(time: 5, unit: 'MINUTES') {
          script {
            echo 'This stage does not block an executor because of "agent none"'
            milestone 1
            inputResponse = input([
              message           : 'Your branch',
              parameters        : [
               string(name: 'Select branch')
              ]
            ])
            milestone 2
            echo "Input response: ${inputResponse}"
          }
        }
      }
    }
 
    stage('Build') {
      agent any
      steps {
        script {
          git(branch: "${inputResponse}", url: "https://github.com/pdrodavi/pipeline-node.git")
          echo "Branch selected: ${inputResponse}"
        }
      }
    }


  }
}
