node{
	stage('SCM Checkout'){
		git branch: 'slacknotification', url: 'https://github.com/suman-stha/devopsprojects.git'
	}
	stage('Compile-Package'){
		def mvnHome = tool name: 'mymaven', type: 'maven'
		sh "${mvnHome}/bin/mvn package"
	}
	stage('Deployment to Tomcat'){
	sshagent(['pem-tomcatser']) {
    sh 'ssh -o StrictHostKeyChecking=no target/*.war ec2-user@52.15.194.138:/opt/tomcat9/webapp/'
}
}

}
