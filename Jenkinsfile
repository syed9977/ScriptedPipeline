node('master') 
{
    stage('Continuous Download') 
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('Continuous Build') 
    {
       sh 'mvn package'
    }
    stage('Continuous Deployment') 
    {
       sh 'scp /home/ubuntu/.jenkins/workspace/ScirptedPipeline/webapp/target/webapp.war ubuntu@172.31.26.43:/var/lib/tomcat8/webapps/testapp.war'
    }
    stage('Continuous Testing') 
    {
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
       sh 'java -jar /home/ubuntu/.jenkins/workspace/ScirptedPipeline/testing.jar'
    }
    stage('Continuous Delivery') 
    {
       sh 'scp /home/ubuntu/.jenkins/workspace/ScirptedPipeline/webapp/target/webapp.war ubuntu@172.31.23.12:/var/lib/tomcat8/webapps/prodapp.war'
    }
   
}
