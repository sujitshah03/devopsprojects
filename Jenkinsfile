node{
 stage('Git Checkout'){
	git branch: 'dockercicd', url: 'https://github.com/prabhatpankaj/devopsprojects.git'  
 }
 stage('Maven Package'){
	def mvnHome = tool name: 'maven-3', type: 'maven'
	sh "${mvnHome}/bin/mvn clean package"
 	sh 'mv target/myweb*.war target/myweb.war'
 }
 
 stage('Build Docker Imager'){
   sh 'docker build -t prabhatiitbhu/myweb:0.0.1 .'
 }
 
}
