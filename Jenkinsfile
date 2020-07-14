node{
 stage('Git Checkout'){
	git branch: 'dockercicd', url: 'https://github.com/prabhatpankaj/devopsprojects.git'  
 }

 stage('Git change file status'){
   sh 'git diff --name-only'
 }
 
}
