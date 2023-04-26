node{
  echo "The Job name is:${env.JOB_NAME}"
  echo "The build number is :${env.BUILD_NUMBER}"
  echo " The  node name is :${env.NODE_NAME}"
  properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
def mavenHome= tool name: 'maven3.9.1'
stage('checkoutCode'){
git branch: 'development', credentialsId: '56df1e26-60c4-4c8d-b1fa-870b362b15e3', url: 'https://github.com/harini5599/maven-web-application.git'
}
stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQueReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}
stage('UPloadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn deploy"

}

stage ('DeployAppintoTomcat'){
sshagent(['harini']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.127.2.211:/opt/apache-tomcat-9.0.73/webapps"

}
}
*/
}
