node{
  stage('SCM Checkout'){
	  git branch: 'wartomcat', url: 'https://github.com/sujitshah03/devopsprojects.git'
  
	}
  
  stage('Compile-Package'){
	 def mvnHome = tool name: 'apache-maven-3.6.3', type: 'maven'
  	 sh "${mvnHome}/bin/mvn package"
	}
}
