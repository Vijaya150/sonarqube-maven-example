pipeline {
    agent any
    
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
        
       stage('SonarQube Analysis') {
    steps {
        withSonarQubeEnv('ServerNameSonar') {
            sh '''
                mvn clean verify sonar:sonar \
                -Dsonar.projectKey=sonar-analysis \
                -Dsonar.projectName=sonar-analysis \
                -Dsonar.host.url=http://56.228.3.46:9000/
            '''
            echo 'SonarQube Analysis Completed'
        }
    }
       }
    }
}
