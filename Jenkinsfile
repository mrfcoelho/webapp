pipeline {
  agent any
  stages {
    stage('Pull Source') {
      steps {
        echo 'Pull source started'
        git(url: 'https://github.com/mrfcoelho/webapp', branch: 'main')
        echo 'Pull source finished'
      }
    }

    stage('Build') {
      steps {
        echo 'Build started'
        sh 'docker build -f app/Dockerfile -t mynginx:latest .'
        echo 'Build finished'
      }
    }

    stage('Run test') {
      steps {
        echo 'Container creation started'
        sh 'docker-compose up --build -d'
        echo 'Container creation finished'
      }

    }

  }
}