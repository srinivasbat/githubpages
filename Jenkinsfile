pipeline {
  agent {
    label 'jenkins-slave' // Specify the Jenkins agent where the pipeline will run
  }
  
  stages {
    stage('Deploy') {
      steps {
        sh 'rm -rf /var/www/html/*' // Remove existing HTML and image files
        sh 'cp /root/workspace/new-pipeline-test/index.html /var/www/html/'
        sh 'cp -r /root/workspace/new-pipeline-test/image/*.png /var/www/html/'
        sh 'cp /root/workspace/new-pipeline-test/style.css /var/www/html/'
      }
    }
    
    stage('BeforeInstall') {
      steps {
        sh 'chmod +x /root/workspace/new-pipeline-test/install_dependencies'
        sh 'chmod +x /root/workspace/new-pipeline-test/start_server'
        sh 'chmod +x /root/workspace/new-pipeline-test/stop_server'
        
        sh '/root/workspace/new-pipeline-test/install_dependencies'
        sh '/root/workspace/new-pipeline-test/start_server'
      }
    }
    
    stage('ApplicationStop') {
      steps {
        sh 'chmod +x /root/workspace/new-pipeline-test/stop_server'
        sh '/root/workspace/new-pipeline-test/stop_server'
      }
    }
  }
}
