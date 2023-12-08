pipeline {
    agent any

    parameters {
        string(name: 'Browsersite', defaultValue: 'Chrome', description: 'Code to run on browser')
    }

<<<<<<< HEAD
    tools {
        maven "MAVEN_HOME"
    }
=======
     tools {
            maven "MAVEN_HOME"
          }
>>>>>>> dce02da9d47c847de2ee7684870efde38ff7c853

    stages {
        stage('Build') {
            steps {
<<<<<<< HEAD
                
                bat 'mvn clean install'
=======
               bat 'mvn clean install'
>>>>>>> dce02da9d47c847de2ee7684870efde38ff7c853
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
