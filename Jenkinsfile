node{
	stage('SCM Checkout'){
		git branch: 'wartomcat', url: 'https://github.com/prabhatpankaj/devopsprojects.git'
	}
	stage('Compile-Package'){
		def mvnHome = tool name: 'maven-3.5.4', type: 'maven'
		sh "${mvnHome}/bin/mvn package"
	}
	stage('Deploy to Tomcat'){
		sshagent(['tomcatserver']) {
		sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@18.136.126.144:/opt/tomcat9/webapps/'
	}
	}
}
