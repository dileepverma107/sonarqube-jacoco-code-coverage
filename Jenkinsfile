pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stage('Initialize')
        {
            def dockerHome = tool 'MyDocker'
            env.PATH = "${dockerHome}/bin:${env.PATH}"
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
        stage('Run Docker Image') {
            steps {
                powershell './gradlew dockerRun'
            }
        }
    }
}