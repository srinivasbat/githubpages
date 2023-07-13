pipeline {
  agent {
    label 'jenkins-slave' // Specify the Jenkins agent where the pipeline will run
  }
  
  stages {
    stage('BeforeInstall') {
      steps {
        sh 'scripts/install_dependencies'
        sh 'scripts/start_server'
      }
    }
    
    stage('Deploy') {
      steps {
        sh 'cp $WORKSPACE/index.html /var/www/html/'
      }
    }
    
    stage('ApplicationStop') {
      steps {
        sh 'scripts/stop_server'
      }
    }
  }
}
