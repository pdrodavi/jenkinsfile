pipeline {
  agent none // agent can only be overwritten if the initial value is 'none'
  stages {

    stage('Stage 1') {
      agent any
      steps {
        script {
          echo 'This stage is blocking the executor because of the "agent any"'
        }
      }
    }

    stage('Stage 2') {
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
            git branch: inputResponse, url: 'https://github.com/pdrodavi/pipeline-node.git'
            echo "Input response: ${inputResponse}"
          }
        }
      }
    }

    stage('Stage 3') {
      agent any
      steps {
        script {
          echo 'This stage is blocking the executor because of the "agent any"'
        }
      }
    }


  }
}
