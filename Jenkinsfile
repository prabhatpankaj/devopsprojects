node{
  stage('SCM Checkout'){
	  git branch: 'wartomcat', url: 'https://github.com/prabhatpankaj/devopsprojects.git'
  
	}
  
  stage('Compile-Package'){
	 def mvnHome = tool name: 'maven-3.6.3', type: 'maven'
  	 sh "${mvnHome}/bin/mvn package"
	}
	
  stage('Deploy to Tomcat'){
		sshagent(['ec2demo.pem'']) {
		sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@35.173.122.38:/opt/tomcat9/webapps/'
	}
}
