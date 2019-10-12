node{
	stage('SCM Checkout'){
		git branch: 'slacknotification', url: 'https://github.com/prabhatpankaj/devopsprojects.git'
	}
	stage('Compile-Package'){
		def mvnHome = tool name: 'maven-3.5.4', type: 'maven'
		sh "${mvnHome}/bin/mvn package"
	}
	stage('Deploy to Tomcat'){
		sshagent(['tomcatserver']) {
		sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@54.169.210.48:/opt/tomcat9/webapps/'
	}
	}
	stage('Slack Notification'){
		slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#intelycore09', color: '#439FE0', message: 'New Build deployed', teamDomain: 'intelycore09', tokenCredentialId: 'slack-secret'
	}
}
