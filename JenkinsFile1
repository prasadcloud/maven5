ipipeline
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
                        git 'https://github.com/prasadcloud/maven2.git'
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
}
}
