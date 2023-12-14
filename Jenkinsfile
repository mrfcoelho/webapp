pipeline {
  agent any
  stages {
    stage('Pull Source') {
      steps {
        git(url: 'https://github.com/mrfcoelho/webapp', branch: 'main')
      }
    }

  }
}