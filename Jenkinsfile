node{
  stage('SCM Checkout'){
	  git branch: 'wartomcat', url: 'https://github.com/sujitshah03/devopsprojects.git'
  
	}
  
  stage('Compile-Package'){
	 def mvnHome = tool name: 'apache-maven-3.6.3', type: 'maven'
  	 sh "${mvnHome}/bin/mvn package"
	}
  stage('Deploy to Tomcat'){
	sshagent(['sujit01']) {
	sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@52.23.163.71:/opt/tomcat9/webapps/'
	}
   }
	
stage('Slack Notification'){
	slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#webapps', color: '#439FE0', message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}", tokenCredentialId: 'slack-secret'
	}
  
}
	
stage('Email Notification'){
	mail bcc: 'a.sujitshah34@gmail.com', body: 'message', cc: 'a.sujitshah34@gmail.com', from: 'anhuman74@gmail.com', replyTo: 'a.sujitshah34@gmail.com', subject: 'message', to: 'a.sujitshah34@gmail.com'
	}
  
}
