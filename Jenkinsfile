node{
  stage('SCM Checkout'){
	  git branch: 'wartomcat', url: 'https://github.com/prabhatpankaj/devopsprojects.git'
  
	}
  
  stage('Compile-Package'){
	 def mvnHome = tool name: 'maven-3.5.4', type: 'maven'
  	 sh "${mvnHome}/bin/mvn package"
	}
  
  stage('Deploy to Tomcat'){
	  sshagent(['jenkins-memo-key']) {
    		sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@100.26.175.204:/opt/tomcat9/webapps/'
	}
	  # sshagent(['jenkins-memo-key']) {
	   # sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@100.26.175.204:/opt/tomcat9/webapps/'
	#}
  
	#}
  
}
