pipeline {
  agent any
  stages {
    stage('Download Environment') {
      parallel {
        stage('Download Environment') {
          steps {
            sh 'wget https://svn.reactos.org/amine/RosBEBinFull.tar.gz -O RosBE.tar.gz'
          }
        }
        stage('error') {
          steps {
            echo 'Downloading...'
          }
        }
      }
    }
    stage('Unarchive') {
      parallel {
        stage('Unarchive') {
          steps {
            sh 'tar -xzf RosBE.tar.gz'
            waitUntil() {
              fileExists 'RosBE'
            }

          }
        }
        stage('error') {
          steps {
            echo 'Unarchiving'
          }
        }
      }
    }
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh 'echo \'mkdir ../Build && cd ../Build && $WORKSPACE/configure.sh -DENABLE_ROSTESTS=1 && cd reactos && ninja -k 0 && ninja bootcd\' > tmp_file'
          }
        }
        stage('error') {
          steps {
            echo 'Building and praying...'
          }
        }
      }
    }
    stage('Done message') {
      steps {
        echo 'It finished!'
      }
    }
  }
}