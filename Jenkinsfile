pipeline
{
    agent any
    stages
    {
        stage('ContinousDownload')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/prasadcloud/maven5.git'
                    }
                    catch(Exception e1)
                    {
                        mail bcc: '', body: 'GIT Admins, Continous Download failed please check therepo', cc: '', from: '', replyTo: '', subject: 'Continous Download Failed', to: 'prasad.cloud85@gmail.com'
                        exit(1)
                    }
                }
            }
        }
                    stage('ContinousBuild')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'mvn package'
                    }
                    catch(Exception e2)
                    {
                        mail bcc: '', body: 'DevTeam, Continous BUild failed please check', cc: '', from: '', replyTo: '', subject: 'Continous Build Failed', to: 'prasad.cloud85@gmail.com'
                        exit(1)
                        
                        
                    }
                }
            }
        }
			stage('ContinousDeploy')
        {
            steps
            {
                script
                {
                    try
                    {
                     sh 'scp /var/lib/jenkins/workspace/MyAVDDeclarativeTryCatch1/webapp/target/webapp.war ubuntu@172.31.26.206:/var/lib/tomcat9/webapps/testAVD.war'
                    }
                    catch(Exception e3)
                    {
                        mail bcc: '', body: 'Middleware, Continous Deploy failed please check', cc: '', from: '', replyTo: '', subject: 'Continous Deploy Failed', to: 'prasad.cloud85@gmail.com'
                        exit(1)
                    }
                }
            }
        }
			stage('ContinousTesting')
        {
            steps
            {
                script
                {
                    try
                    {
                     git 'https://github.com/prasadcloud/FunctionalTesting.git'
					 sh 'java -jar /var/lib/jenkins/workspace/MyAVDDeclarativeTryCatch1/testing.jar'
                    }
                    catch(Exception e4)
                    {
                        mail bcc: '', body: 'TestTeam, Continous Test failed please check', cc: '', from: '', replyTo: '', subject: 'Continous Test Failed', to: 'prasad.cloud85@gmail.com'
                        exit(1)
                    }
                }
            }
        }
		stage('ContinousDelivery')
        {
            steps
            {
                script
                {
                    try
                    {
                     sh 'scp /var/lib/jenkins/workspace/MyAVDDeclarativeTryCatch1/webapp/target/webapp.war ubuntu@172.31.21.142:/var/lib/tomcat9/webapps/prodAVD.war'
                    }
                    catch(Exception e5)
                    {
                        mail bcc: '', body: 'DeliveryTeam, Continous Delivery failed please check', cc: '', from: '', replyTo: '', subject: 'Continous Delivery Failed', to: 'prasad.cloud85@gmail.com'
                    }
                }
            }
        }
    }
}

