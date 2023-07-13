pipeline {
  agent {
    label 'jenkins-slave' // Specify the Jenkins agent where the pipeline will run
  }
  
  stages {
    stage('Deploy') {
      steps {
        sh 'cp /root/workspace/pipeline-test/codedeploy-master/index.html /var/www/html/'
        sh 'cp /root/workspace/pipeline-test/codedeploy-master/*.jpg /var/www/html/'
      }
    }
    
    stage('BeforeInstall') {
      steps {
        sh 'chmod +x /root/workspace/pipeline-test/codedeploy-master/scripts/install_dependencies'
        sh 'chmod +x /root/workspace/pipeline-test/codedeploy-master/scripts/start_server'
        sh 'chmod +x /root/workspace/pipeline-test/codedeploy-master/scripts/stop_server'
        
        sh '/root/workspace/pipeline-test/codedeploy-master/scripts/install_dependencies'
        sh '/root/workspace/pipeline-test/codedeploy-master/scripts/start_server'
      }
    }
    
    stage('ApplicationStop') {
      steps {
        sh 'chmod +x /root/workspace/pipeline-test/codedeploy-master/scripts/stop_server'
        sh '/root/workspace/pipeline-test/codedeploy-master/scripts/stop_server'
      }
    }
  }
}
