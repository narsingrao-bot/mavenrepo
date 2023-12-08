pipeline {
    agent any

    parameters {
        string(name: 'Browsersite', defaultValue: 'Chrome', description: 'Code to run on browser')
    }

    tools {
        maven "MAVEN_HOME"
    }

    stages {
        stage('Build') {
            steps {
                
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                script {
                    bat "mvn clean test -DBrowser=${Browsersite}"
                  //  bat "mvn -Dmaven.test.failure.ignore=true clean package"
                }
            }
        }
    }

    post {
        success {
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
        }
    }
}
