node{
	stage('SCM Checkout'){
		git branch: 'slacknotification', url: 'https://github.com/suman-stha/devopsprojects.git'
	}
	stage('Compile-Package'){
		def mvnHome = tool name: 'mymaven', type: 'maven'
		sh "${mvnHome}/bin/mvn package"
	}
	stage('Slack Notification'){
	slackSend baseUrl: 'https://hooks.slack.com/services/',
     channel: '#devops', color: '#008000', 
     message: 'Build Started', 
     teamDomain: 'devops-dxa2539', 
     tokenCredentialId: 'slack-secret'
	}

}
