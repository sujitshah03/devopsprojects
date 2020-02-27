node{
  stage('SCM Checkout'){
	  git branch: 'wartomcat', url: 'https://github.com/prabhatpankaj/devopsprojects.git'
  
	}
  
  stage('Compile-Package'){
	 def mvnHome = tool name: 'maven-3.5.4', type: 'maven'
  	 sh "${mvnHome}/bin/mvn package"
	}
  
  stage('Deploy to Tomcat'){
	  sshagent(['tomcat-dev']) {
	    sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@18.234.143.115:/opt/tomcat9/webapps/'
	}
  
	}
	
stage('Slack Notification'){
	slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#jenkinsnotification', color: '#fc0324', message: 'New Build deployed by prabhat', teamDomain: 'intelycoreworkspace', tokenCredentialId: 'slack-secret'
	}
	
stage('Email Notification'){
	mail bcc: '', body: 'build success done', cc: '', from: 'prabhat@aptence.com', replyTo: 'prabhatiitbhu@gmail.com', subject: 'build success', to: 'prabhat@aptence.com'
	}
  
}
