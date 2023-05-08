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
             deploy adapters: [tomcat9(credentialsId: '89f2d959-95ba-4850-9e44-28989d68e05b', path: '', url: 'http://172.31.31.66:8080')], contextPath: 'testapp2', war: '**/*.war'
            }
        }
        stage('ContinousTesting')
        {
            steps
            {
             git 'https://github.com/prasadcloud/FunctionalTesting.git'
             sh 'java -jar /var/lib/jenkins/workspace/MyAVDDeclarative1/testing.jar'
            }
        }
            stage('ContinousDelivery')
        {
            steps
            {
             
             input message: 'Please approve deployment', submitter: 'srinivas'
             sh 'scp /var/lib/jenkins/workspace/MyAVDDeclarative1/webapp/target/webapp.war  ubuntu@172.31.23.145:/var/lib/tomcat9/webapps/prod1.war'
            }
        }
    }
}
