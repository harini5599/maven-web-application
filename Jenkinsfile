node
{
 
 def mavenHome = tool name: "maven3.8.1"
 
 properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
 
 stage('CheckoutCode')
 {
 git branch: 'development', credentialsId: '6773dc34-a3fd-44ec-b1ee-3d2f0aa9f346', url: 'https://github.com/MithunTechnologiesDevOps/maven-web-application.git'
 }
 
 stage('Build')
 {
 sh "${mavenHome}/bin/mvn clean package"
 }
 /*
 stage('ExecuteSonarQubeReport')
 {
 sh "${mavenHome}/bin/mvn sonar:sonar"
 }
 
 stage('UploadArtifactsintoNexus')
 {
 sh "${mavenHome}/bin/mvn deploy"
 }
 
  stage('DeployAppintoTomcatServer')
 {
 sshagent(['017ba0e8-c08f-46e9-94aa-834371229478']) {
 sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@52.64.130.198:/opt/apache-tomcat-9.0.45/webapps/"
 }
 }
*/
 stage('SendEmailNotification')
 {
 emailext body: '''Build Over..

 Regards,
 Mithun Technologies,
 9980923226''', subject: 'Build Over...', to: 'devopstrainingblr@gmail.com'
 }


}
