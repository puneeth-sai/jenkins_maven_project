pipeline {
    agent any 
    stages {
        stage('clean compile') { 
            steps {

                sh "mvn clean"
                sh "mvncompile"

            }
        }
        stage('Test') { 
            steps {
                sh "mvn test"
            }
        }
        stage('Deploy') { 
            steps {
                sh "mvn package" 
            }
        }

        stage('Archiving') { 
            steps {
                 archivingArtifacts '**/target/*.jar' 
            }
        }
    }
}
