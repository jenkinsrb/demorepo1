pipeline {
  agent any
  stages {
    stage('buildStage') {
      steps {
        git(url: 'https://github.com/jenkinsrb/demorepo1', branch: 'master', credentialsId: '0f45a68c-1fba-495c-a168-f427ee6d257f')
        sh 'docker build -t jenkinsrb/jenkinsrepo1:latest .'
      }
    }

    stage('DEV&QA') {
      parallel {
        stage('DevDeploy') {
          steps {
            sh 'docker push jenkinsrb/jenkinsrepo1:latest'
          }
        }

        stage('DeployQA') {
          steps {
            echo 'QA Deploy Done'
          }
        }

      }
    }

  }
}