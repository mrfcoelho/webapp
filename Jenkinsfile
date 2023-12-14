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
        sh 'docker build -f app/Dockerfile -t mrfcoelho/mynginx:latest app/'
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

     stage('Push to Dockerhub') {
      environment {
        DOCKERHUB_CREDENTIALS=credentials('dockerhubmc')
      }
      steps {
        echo 'Trying to log into Dockerhub'
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        echo 'Successfully logged into Dockerhub'
        echo 'Trying to push image into Dockerhub'
        sh 'docker push mrfcoelho/mynginx:latest'
        echo 'Successfully pushed image into Dockerhub'
      }
    }

  }
}