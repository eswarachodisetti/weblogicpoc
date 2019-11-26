pipeline {
  options {
    disableConcurrentBuilds()
  }
  agent {
    label "jenkins-jx-base"
  }
  environment {
    DEPLOY_NAMESPACE = "default"
  }
  stages {
    
  /*  
     stage('Build') {
      steps {
        container('jx-base') {
          sh 'docker build -t dhanapodigiri/poclistener:6.0 .'
		      sh 'docker images'
	
        }

      }
    }
    
    
    	  
    stage('Push') {
		steps{
			script {
				container('jx-base') {
				
					sh 'mount -o remount,rw /home/jenkins/.docker'
					sh 'scp ${WORKSPACE}/config.json /home/jenkins/.docker/'
					sh 'docker push dhanapodigiri/poclistener:6.0'	
				}
			
			}
		}
	}
*/     
	
    
    stage('Deployment') {
      steps {
        container('jx-base') {
          dir('weblogicpoc') {
		sh 'kubectl get namespaces'
            //   sh 'jx step helm apply --name weblogicpoc'
        
       
       }
        }

      }
    }
  }
}
