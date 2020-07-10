pipeline {
  agent any
  stages {
    stage('stage1') {
      agent {
        docker {
          image 'busybox:latest'
          args '-p 80:80'
        }

      }
      environment {
        host = 'docker-stage1'
      }
      steps {
        sh 'echo "stage1 test"'
      }
    }

    stage('stage2') {
      parallel {
        stage('stage2') {
          agent {
            node {
              label 'stage-2-1'
            }

          }
          steps {
            sh 'hostname'
          }
        }

        stage('') {
          agent {
            dockerfile {
              filename 'Dockerfile'
            }

          }
          environment {
            docker = 'file-stage-2-2'
          }
          steps {
            echo 'stage-2-2'
          }
        }

      }
    }

    stage('') {
      steps {
        echo 'stage-3'
      }
    }

    stage('stage4') {
      agent {
        docker {
          image 'alphie'
        }

      }
      environment {
        docker4 = 'stage4'
      }
      steps {
        sh 'echo "end"'
      }
    }

  }
}