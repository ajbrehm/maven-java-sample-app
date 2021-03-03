Skip to content
Search or jump to…

Pull requests
Issues
Marketplace
Explore
 
@ajbrehm 
saurabhd2106
/
maven-java-sample-app
1
01
Code
Issues
Pull requests
Actions
Projects
Wiki
Security
Insights
maven-java-sample-app/Jenkinsfile
@saurabhd2106
saurabhd2106 Update Jenkinsfile
Latest commit 5a89cba 3 minutes ago
 History
 1 contributor
48 lines (35 sloc)  895 Bytes
  
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

         post {
            always {
                junit 'target/surefire-reports/TEST-*.xml'
            }
            success {
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
        
        }

        stage('Deploy'){
            steps {

                withEnv(['JENKINS_NODE_COOKIE=dontKillMe']) {

                powershell 'java "-Dserver.port=8001" -jar target/spring-petclinic-2.3.1.BUILD-SNAPSHOT.jar'

                }
            }
        }
    }



}
© 2021 GitHub, Inc.
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About
