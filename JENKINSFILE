node{

echo "The Job name is: ${env.JOB_NAME}"
echo "The build number is: ${env.BUILD_NUMBER}"
echo "The Node name is: ${env.NODE_NAME}"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
def mavenHome = tool name: "maven3.9.4"
stage('checkoutcode'){
git branch: 'development', credentialsId: '739d7ad4-e60a-4e62-9683-2de6172a9cea',
url: 'https://github.com/mss-morning-projects/maven-web-application.git'
}
stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployAppIntoTomcat'){
sshagent(['e3377d48-bad3-4d9e-a8e1-e8006a63f3b2']) {
     sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.33.15:/opt/apache-tomcat-9.0.82/webapps/
"
}
}
*/
}
