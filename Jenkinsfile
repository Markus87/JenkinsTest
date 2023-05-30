pipeline{
    agent{
        label 'Windows'
    }
    options{ 
        disableConcurrentBuilds()
    }	
    stages{
        stage('Delay'){
            steps{
                powershell '''ping -n 300 127.0.0.1 '''
            }
            post{
                success{
                    emailext body: "Test.\n${env.BUILD_URL}", subject: 'Test Jenkins', to: "Reaper@sags-per-mail.de"
                }
            }               
        }
    }
}