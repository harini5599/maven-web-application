node{
def mavenHome= tool name: 'maven3.9.1'
stage('checkoutCode'){
git branch: 'development', credentialsId: '56df1e26-60c4-4c8d-b1fa-870b362b15e3', url: 'https://github.com/harini5599/maven-web-application.git'
}
stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
stage('ExecuteSonarQueReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}
stage('UPloadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn deploy"

}stage ('DeployAppintoTomcat'){
sshagent(['83b02926-7492-4205-8ad3-d8e27ce8b373']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.40.205:/opt/apache-tomcat-9.0.73/webapps"
}
}

}
