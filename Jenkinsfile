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
    stages
    {
        stage('SCM_checkout')
        {
            steps
            {
                checkout scmGit(branches: [[name: 'stable-2.289']],
                userRemoteConfigs: [
                    [ url: 'https://github.com/jenkinsci/jenkins.git' ]
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