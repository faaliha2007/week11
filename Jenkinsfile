pipeline {
    agent any

    stages {
        stage('Pull Code') {
            steps {
                checkout scm
            }
        }
        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        stage('Run Application') {
            steps {
                bat 'java -jar target/dvp-week11-cicd-1.0.jar'
            }
        }
    }
    post {
        success { echo 'DVP WEEK 11 BUILD SUCCESSFUL!' }
        failure { echo 'DVP WEEK 11 BUILD FAILED!' }
    }
}
