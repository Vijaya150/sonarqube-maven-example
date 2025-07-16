pipeline {
    agent { label 'testlabel1' }
    
    tools {
        maven 'Maven'     
        jdk 'JDK17' 
    }
    
    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Git branch to build')
    }
    
    stages {
        stage('Git checkout') {
            steps {
                echo "Checking out branch: ${params.BRANCH_NAME}"
                git branch: "${params.BRANCH_NAME}", url: "https://github.com/Vijaya150/sonarqube-maven-example.git"
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
