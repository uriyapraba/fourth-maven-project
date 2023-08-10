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
                sh 'mvn clean package'
            }
        }
        stage('sonar code quality')
        {
            steps
            {
                //def scannerHome = tool 'SonarScanner-5.0.1';
                withSonarQubeEnv('sonarqube-10.1')
                {
                //sh "${scannerHome}/bin/sonar-scanner"
                sh 'mvn sonar:sonar'
                }
            }
            
        }
    }
}