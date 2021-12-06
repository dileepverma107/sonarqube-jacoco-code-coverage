pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                powershell 'gradle assemble'
            }
        }
         stage('Test') {
            steps {
                powershell 'gradle test'
            }
        }
        stage('Build Docker Image') {
            steps {
                powershell 'gradle docker'
            }
        }
        stage('Run Docker Image') {
            steps {
                powershell 'gradle dockerRun'
            }
        }
    }
}