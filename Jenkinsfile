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
}
