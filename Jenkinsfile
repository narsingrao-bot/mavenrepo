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
            script {
                    // Pass Browsersite as an environment variable to Maven
                    withEnv(["BROWSER=${Browsersite}"]) {
                        bat 'mvn clean install'
                    }

            } 
        }
        stage('Test') {
            steps {
                script {
                    // Pass Browsersite as an environment variable to Maven
                    withEnv(["BROWSER=${Browsersite}"]) {
                        bat "mvn clean test"
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
}