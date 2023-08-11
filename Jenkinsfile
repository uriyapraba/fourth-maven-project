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
        stage('Sonar-code-quality')
        {
            steps
            {
                sh 'pwd; ls -lrt'
                withSonarQubeEnv('sonarqube-10.1')
                {
                    sh 'mvn clean verify sonar:sonar \
                        -Dsonar.projectKey=maven-project \
                        -Dsonar.projectName='maven-project' \
                        -Dsonar.host.url=http://54.253.191.10:9000 \
                        -Dsonar.token=sqp_d8b3e80202a86e4599633d23f74d1a228039ad58'
                }
            }
        }
    }
}