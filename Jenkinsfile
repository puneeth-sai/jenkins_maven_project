pipeline {
    agent any 
    stages {
        stage('Clean') { 
            steps {
                sh "printenv"
                sh "mvn clean"      
            }
        }
         stage('compile') { 
            steps {
                sh "mvn compile"      
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
                archiveArtifacts '**/target/*.jar'
            }
        }
    }
}
