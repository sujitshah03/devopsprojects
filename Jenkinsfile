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
	    sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@100.26.202.223:/opt/tomcat9/webapps/'
	}
  
	}
	
stage('Slack Notification'){
	slackSend baseUrl: 'https://hooks.slack.com/services/', channel: 'jenkinsdemo', color: '"#439FE0"', message: 'started ${env.JOB_NAME} ${env.BUILD_NUMBER}', teamDomain: 'aptence', tokenCredentialId: 'slack-secret'
	}
  
}
