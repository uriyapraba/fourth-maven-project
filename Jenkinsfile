/*pipeline
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
}*/
/**********Pipeline-Maven-Sonarqube-slave-system**************/
pipeline
{
    agent
    {
        node
        {
            label 'slave1'
        }
    }
    tools
            {
                maven 'maven_3.9.4'
            }
    stages
    {
        stage('SCM_Checkout')
        {
            steps
            {
                checkout scmGit(branches: [[name: 'origin/maven-sonar-build']],
                userRemoteConfigs: [
                    [ url: 'https://github.com/uriyapraba/fourth-maven-project.git' ]
                ])
            }
        }
        stage('maven_build')
        {
            steps
            {
                sh 'mvn clean package'
            }
        }
        stage('code-quality')
        {
            steps
            {
               withSonarQubeEnv('sonarqube-10.1')
                {
                //sh "${scannerHome}/bin/sonar-scanner"
                sh 'mvn clean verify sonar:sonar \
                    -Dsonar.projectKey=jenkins-intergration-key \
                    -Dsonar.host.url=http://192.168.55.51:9000 \
                    -Dsonar.login=sqp_a8109ea66ee26d41edf3c36dcedb5ef3aab17e8f'
                } 
            }
        }
    }
}