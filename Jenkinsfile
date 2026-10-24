pipeline {
    agent any
    tools {
        maven 'Maven3'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
    }
    post {
        success {
            archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: false
        }
    }
}
