
node {
   // This is to demo github action	
   def sonarUrl = 'sonar.host.url=http://172.26.0.3:9000'
   def mvn = tool (name: 'maven3', type: 'maven') + '/bin/mvn'
   stage('SCM Checkout'){
    // Clone repo
	git branch: 'master', 
	credentialsId: 'github_ed', 
	url: 'https://github.com/edsherwin/my-app.git'
   
   }
   
   stage('Sonar Publish'){
	   withCredentials([string(credentialsId: 'sonarqube', variable: 'sonarToken')]) {
        def sonarToken = "sonar.login=${sonarToken}"
        sh "${mvn} sonar:sonar -D${sonarUrl}  -D${sonarToken}"
	 }
      
   }
  
}

