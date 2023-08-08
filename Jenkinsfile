pipeline
{
    agent
    {
        label 'slave1'
    }
    tools
            {
                maven 'maven-3.9.4'
            }
    stages
    {
        stage('SCM_CHECKOUT')
        {
            steps
            {
                checkout scmGit(branches: [[name: 'origin/master']],
                userRemoteConfigs: [
                    [ url: 'https://github.com/uriyapraba/fourth-maven-project.git' ]
                ])
            }
        }
        stage('Maven_Build')
        {
            
            steps
            {
                sh "pwd ; ls -lrt" 
                sh 'mvn compile'
            }
        }
    }
}