node 
{
stage('Project Name')
{
echo 'This is Opstree CI CD'
}

stage('Checkout Code')
{
git 'https://github.com/AshutoshKumar99/CompleteCICDPipeline'
}

stage('Build Code')
{

sh 'mvn clean install -Dmaven.test.failure.ignore=true'
}

stage ('JUnit report')
{
    archive "target/**/*"
    junit 'target/surefire-reports/*.xml' 
}


 
 
 stage('Slage notification')
 {
 
 slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#jenkinspipelinedemo', color: 'good', message: 'Welcome to jenkins, slack !', teamDomain: 'Ashutosh DevOps', tokenCredentialId: 'slackdemo'

 
 }
 
  stage('Deploy to Tomcat'){
      
      sshagent(['TOMCATDEV']) 
      {
	  
	    sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@13.233.162.181:/var/lib/tomcat8/webapps/'
    
}
   }
  
  

}
