pipeline {
  agent any
  stages {
    stage('Parallel execution') {
      parallel {
        stage('Say hello') {
          steps {
            sh 'echo "Hej verden"'
          }
        }

        stage('Build app') {
          agent {
            docker {
              image 'gradle:jdk11'
            }

          }
          steps {
            sh 'ls'
            sh 'ci/build-app.sh'
            archiveArtifacts 'app/build/libs/'
            DeleteDir()
            sh 'ls'
          }
        }

      }
    }

  }
}
