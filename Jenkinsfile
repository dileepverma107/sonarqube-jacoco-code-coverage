pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat './gradlew clean build'
            }
        }
         stage('Test') {
            steps {
                bat './gradlew test'
            }
         }
        stage('SonarQube Analysis') {
            steps {
                script {
                    withSonarQubeEnv(credentialsId:'sonar-token') {
                       bat './gradlew sonarqube --warning-mode=all'
                    }
                    
                    timeout(time:1 , unit:HOURS) {
                        def gg = waitForQualityGate() 
                        if (gg.status != OK) {
                            error "Pipeline aborted due to quality gate failure: ${gg.status}"
                        }
                    }
                }
            }
        }
    }
}
