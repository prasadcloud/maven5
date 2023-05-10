pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload'){
            
        
        steps
        {
            git 'https://github.com/prasadcloud/maven2.git'
        }
       }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeploy')
        {
            steps
            {
             sh 'scp /var/lib/jenkins/workspace/MyAVDShared2/webapp/target/webapp.war ubuntu@172.31.26.206:/var/lib/tomcat9/webapps/testAVD1.war'
            }
        }
        stage('ContinousTesting')
        {
            steps
            {
             git 'https://github.com/prasadcloud/FunctionalTesting.git'
             sh 'java -jar /var/lib/jenkins/workspace/MyAVDShared2/testing.jar'
            }
        }
            stage('ContinousDelivery')
        {
            steps
            {
             
             sh 'scp /var/lib/jenkins/workspace/MyAVDShared2/webapp/target/webapp.war  ubuntu@172.31.21.142:/var/lib/tomcat9/webapps/prod1.war'
            }
        }
    }
}
