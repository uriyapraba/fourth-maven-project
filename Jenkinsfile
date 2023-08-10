pipeline
{
    agent any
    tools
            {
                maven 'maven_3.9.4'
            }
    stages
    {
        stage('SCM_CHECKOUT')
        {
            steps
            {
                checkout scmGit(branches: [[name: 'origin/sonar-build']],
                userRemoteConfigs: [
                    [ url: 'https://github.com/uriyapraba/fourth-maven-project.git' ]
                ])
            }
        }
        stage('Maven_Build')
        {
            
            steps
            {
                sh 'pwd'
                sh 'mvn clean verify'
            }
        }
    }
}