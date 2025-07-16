pipeline {
    agent { label 'testlabel1'}
    
    tools {
        maven 'Maven'     
        jdk 'JDK17' 
    }
    
    stages{
        stage('Git checkout'){
            steps{
                git url: "https://github.com/Vijaya150/sonarqube-maven-example.git"
            }
        }
        stage('Build Info') {
            steps {
                echo "Building branch: ${params.BRANCH_NAME}"
            }
        }
       stage('SonarQube Analysis') {
    steps {
        withSonarQubeEnv('ServerNameSonar') {
            sh '''
                mvn clean verify sonar:sonar \
                -Dsonar.projectKey=sonar-analysis \
                -Dsonar.projectName=sonar-analysis \
                -Dsonar.host.url=http://16.16.167.86:9001/
            '''
            echo 'SonarQube Analysis Completed'
        }
    }
       }
    }
}
