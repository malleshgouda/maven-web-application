node{

def mavenHome  =  tool name:  "maven3.8.6"

echo "Build number: ${env.Build_NUMBER}"
echo "Job name is : ${env.JOB_NAME}"
echo " Node name is : ${env.NODE_NAME}"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

stage( ' CheckoutCode ') {
git credentialsId: '8ce95c32-881e-47bf-bad4-cb29d40a0500', url: 'https://github.com/malleshgouda/maven-web-application.git'
}

stage( ' Build '){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage('UploadArtifactintoNexus'){
sh "${mavenHome}/bin/mvn deploy"
}
stage('DeployAppIntoTomcatServer'){
sshagent(['b7a73b5f-09be-4b37-bba3-f069be9f8fba']) {
    // some block
sh  "scp -o StrictHostKeyChecking=no target/maven-web-application.war  ec2-user@172.31.6.237:/opt/apache-tomcat-9.0.69/webapps/"
}
}
*/
}//Node closing
