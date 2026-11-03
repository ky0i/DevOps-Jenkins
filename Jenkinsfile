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
        stage('Deploy to Nexus') {
            steps {
                sh '''
                curl -v -f -u "admin:-G#UUMS8Qi@A" \
                     --upload-file target/accessing-data-mysql-initial-0.0.1-SNAPSHOT.jar \
                     http://host.docker.internal:8081/repository/springboot-repo/accessing-data-mysql-initial-0.0.1-SNAPSHOT.jar
                '''
            }
        }
    }
    post {
        success {
            archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: false
        }
    }
}