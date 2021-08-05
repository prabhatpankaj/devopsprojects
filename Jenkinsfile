node{
  stage('SCM Checkout'){
	  git branch: 'wartomcat', url: 'https://github.com/prabhatpankaj/devopsprojects.git'
  
	}
  
  stage('Compile-Package'){
	 def mvnHome = tool name: 'maven', type: 'maven'
  	 sh "${mvnHome}/bin/mvn package"
	}
	
  stage('Deploy to Tomcat'){
		sshagent(['tomcat-server']) {
		sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@65.0.29.55:/opt/tomcat9/webapps/'
		}
  }
}
