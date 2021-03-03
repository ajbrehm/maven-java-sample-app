pipeline {
    agent any

    stages {
        stage('Build'){
            steps {
                powershell 'mvn compile'
            }
        }

        stage('Test'){
            steps {
                powershell 'mvn test'
            }
        }

        stage('Package'){
            steps {
                powershell 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                powershell '& java -jar -Dserver.port=8001 spring-petclinic-2.3.1.BUILD-SNAPSHOT.jar'
            }
        }

    }

    post {
        always {
            junit 'target/surefire-reports/TEST-*.xml'
        }
        success {
            archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
        }
    }

}
