pipeline {
    agent any

    parameters{
        string(name: 'Browsersite', defaultvalue: 'Chrome', description: 'code run on browser')
    }

    tools {
       
        maven "MAVEN_HOME"
    }

    stages {
        stage('Build') {
            steps {
                

                bat 'mvn clean install'
            
               //  bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
       stage('test') {
            steps {
                
                when{
                    expression{
                        bat "mvn clean test -DBrowser=${Browsersite}"
                        bat "mvn -Dmaven.test.failure.ignore=true clean package"
                        
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
}
