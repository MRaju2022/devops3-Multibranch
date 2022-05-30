pipeline
{
    agent any
    
        stages
        {
            stage('ContinuousDownload')
            {
                steps
                {
                    script
                    {
                        try
                        {
                            git 'https://github.com/MRaju2022/DevOps3.git'
                        }
                        catch(Exception e)
                        {
                            mail bcc: '', body: 'Git download failed', cc: '', from: '', replyTo: '', subject: 'Download issue', to: 'gitadmin@gmail.com'
                        }
                    }
                    
                }
            }
            stage('ContinuousBuild')
            {
                steps
                {
                    script
                    {
                        try
                        {
                            sh 'mvn package'
                        }
                        catch(Exception e)
                        {
                            mail bcc: '', body: 'Unable to build the code', cc: '', from: '', replyTo: '', subject: 'build issue', to: 'devteam@gmail.com'
                        }
                    }
                    
                }
            }
            stage('ContinuousDeploy')
            {
                steps
                {
                     script
                    {
                        try
                        {
                            sh 'scp /home/ubuntu/.jenkins/workspace/DeclartivePipeline/webapp/target/webapp.war ubuntu@172.31.31.201:/var/lib/tomcat9/webapps/qaenv.war'
                        }
                        catch(Exception e)
                        {
                            mail bcc: '', body: 'Deployment failed', cc: '', from: '', replyTo: '', subject: 'deployment issue', to: 'middleware@gmail.com'
                        }
                    }
                    
                }
            }
            stage('ContinuousTesting')
            {
                steps
                {
                     script
                     {
                        try
                        {
                             git 'https://github.com/MRaju2022/Testing.git'
                             sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclartivePipeline/testing.jar'
                        }
                        catch(Exception e)
                        {
                            mail bcc: '', body: 'testing failed', cc: '', from: '', replyTo: '', subject: 'testing issue', to: 'QATeam@gmail.com'
                        }
                    }
                   
                }
            }
             stage('ContinuousDelivery')
            {
                steps
                {
                    script
                     {
                        try
                        {
                             sh 'scp /home/ubuntu/.jenkins/workspace/DeclartivePipeline/webapp/target/webapp.war ubuntu@172.31.25.75:/var/lib/tomcat9/webapps/prodenv.war'
                        }
                        catch(Exception e)
                        {
                            mail bcc: '', body: 'prod deployment failed', cc: '', from: '', replyTo: '', subject: 'prod issue', to: 'deliveryTeam@gmail.com'
                        }
                    }
                    
                }
            }
        }
    
}
