pipeline {
  agent any
  stages {
    stage('Download Environment') {
      steps {
        sh 'wget https://svn.reactos.org/amine/RosBEBinFull.tar.gz -O RosBE.tar.gz tar -xzf RosBE.tar.gz'
        sh 'tar -xzf RosBE.tar.gz'
      }
    }
    stage('Configure and build') {
      steps {
        sh 'echo \'mkdir ../Build && cd ../Build && $WORKSPACE/configure.sh -DENABLE_ROSTESTS=1 && cd reactos && ninja -k 0 && ninja bootcd\' > tmp_file'
      }
    }
  }
}