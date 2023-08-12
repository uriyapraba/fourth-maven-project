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
                sh 'mvn clean install'
            }
        }
        stage('Sonar-code-quality')
        {
            environment
            {
                ACCESS_KEY = credentials('sonarqube-cred')
            }
            steps
            {
                sh 'pwd; ls -lrt'
                withSonarQubeEnv('sonarqube-10.1')
                {
                    /*sh "mvn sonar:sonar \
                    -Dsonar.projectKey=maven-project \
                    -Dsonar.projectName='maven-project' \
                    -Dsonar.host.url=http://13.236.52.185:9000 \
                    -Dsonar.token=${ACCESS_KEY}"*/
                    sh "mvn sonar:sonar"
                }
            }
        }
    }
}