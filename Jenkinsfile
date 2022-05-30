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
            
        }
    
}
