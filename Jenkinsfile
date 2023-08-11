pipeline
{
    agent
    {
        node
        {
            label 'slave1'
            customWorkspace '/home/jenkins/maven-build'
            
        }
    }
    tools
        {
            maven 'maven_3.9.4'
        }
        
    stages
    {
        stage('SCM_checkout')
        {
            steps
            {
                checkout scmGit(branches: [[name: 'origin/maven-sonar-build1']],
                userRemoteConfigs: [
                    [ url: 'https://github.com/uriyapraba/fourth-maven-project.git' ]
                ])
            }
        }
        stage('maven-build')
        {
            steps
            {
                sh 'mvn clean package'
            }
        }
    }
}