pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                powershell './gradlew assemble'
            }
        }
         stage('Test') {
            steps {
                powershell './gradlew test'
            }
        }
        stage('Build Docker Image') {
            steps {
                powershell './gradlew docker'
            }
        }
       /* stage('Run Docker Image') {
            steps {
                powershell './gradlew dockerRun'
            }
        }*/
        stage('Sonar Analysis') {
                    steps {
                        powershell './gradlew sonarqube'
                    }
                }
    }
}
