
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
                bat '"C:\\Users\\Faaliha\\Downloads\\apache-maven-3.9.16-bin\\apache-maven-3.9.16\\bin\\mvn.cmd" clean package'
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
        success {
            echo 'DVP WEEK 11 BUILD SUCCESSFUL!'
        }
        failure {
            echo 'DVP WEEK 11 BUILD FAILED!'
        }
    }
}
