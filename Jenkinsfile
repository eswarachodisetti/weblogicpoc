pipeline {
  options {
    disableConcurrentBuilds()
  }
  agent {
    label "jenkins-jx-base"
  }
  environment {
  //  DEPLOY_NAMESPACE = "default"
    DEPLOY_NAMESPACE = "jx-staging"
    VERSION = "1.0.0-$BUILD_NUMBER"
  }
  stages {
    
  
     stage('Build') {
      steps {
        container('jx-base') {
          sh 'docker build -t dhanapodigiri/poclistener:$VERSION .'
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
					sh 'docker push dhanapodigiri/poclistener:$VERSION'	
				}
			
			}
		}
	}
   
	
   /* 
    stage('Deployment') {
      steps {
        container('jx-base') {
          dir('weblogicpoc') {
		//sh 'kubectl -n jx-production scale deployment pksjenkins --replicas=0'
		  sh 'kubectl apply -f deployment.yaml'
            //   sh 'jx step helm apply --name weblogicpoc'
				}
			}
		}
		}
	*/
  }
}
