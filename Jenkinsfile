node
{

def mavenHome=tool name: "maven-3.6.3"
def buildno = BUILD_NUMBER
/*
echo "github BranchName ${env.BRANCH_NAME}"
echo "Job Number ${env.BUILD_NUMBER}"
echo "Job Name ${env.JOB_NAME}"


properties([[$class: 'JiraProjectProperty'], buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
*/
    
    
stage('github')
{
    git branch: 'development', credentialsId: 'fb389119-b90a-4eb0-aba2-414a22cd84e2', url: 'https://github.com/prathap-jana/maven-web-application.git'
}

stage('build')
{
    sh "${mavenHome}/bin/mvn clean package"
}
    
 stage('Build Docker Image')
    
    {
        sh "docker build -t prathapdockerhub/java-web-app-docker:${buildno} ." 
    }
 
/*
stage('sonarqube')
{
    sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage('nexus')
{
    sh "${mavenHome}/bin/mvn deploy"
}



stage('tomact')
{

sshagent(['cc077986-93c8-49a5-8e7e-ad82222124f8']) {
    
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.233.20.94://opt/apache-tomcat-9.0.31/webapps/"
}

}
*/

}
