node{
  stage('SCM Checkout'){
	  git branch: 'wartomcat', url: 'https://github.com/prabhatpankaj/devopsprojects.git'
  
	}
  
  stage('Compile-Package'){
	 def mvnHome = tool name: 'maven-3.5.4', type: 'maven'
  	 sh "${mvnHome}/bin/mvn package"
	}
	
	stage('deploy to Tomcat') {
		sh 'scp -i /home/ec2-user/jenkins-demo.pem -o StrictHostKeyChecking=no target/*.war ec2-user@100.26.175.204:/opt/tomcat9/webapps/'
	}
  
  
}
