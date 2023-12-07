pipeline {
    agent any

    tools {
       
        maven "MAVEN_HOME"
    }

    stages {
        stage('Build') {
            steps {
                
                git 'https://github.com/jglick/simple-maven-project-with-tests.git'

                // Run Maven on a Unix agent.
               // sh "mvn -Dmaven.test.failure.ignore=true clean package"

                 To run Maven on a Windows agent, use
                 bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            post {
                
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
