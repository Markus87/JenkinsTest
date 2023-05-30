pipeline{
    agent{
        label 'Windows'
    }
    options{ 
        disableConcurrentBuilds()
		throttleJobProperty(
			categories: ['test_limit1'],
			throttleEnabled: true,
			throttleOption: 'category'
		)
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