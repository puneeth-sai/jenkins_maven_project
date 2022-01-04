pipeline {
    agent any 
    stages {
        stage('Clean') { 
            steps {
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
        stage('build') { 
            steps {
                sh "mvn package"
            }
        }
        stage('Archiving') { 
            steps {
                archiveArtifacts '**/target/*.jar'
            }
        }
        stage('deploy') { 
            steps {
                 sshagent(['tomcat-new']) {
                sh """
                    scp -o StrictHostKeyChecking=no target/myweb.war  ec2-user@13.235.247.217:/home/ec2-user/apache-tomcat-9.0.56/webapps/
                    
                    ssh ec2-user@13.235.247.217 /home/ec2-user/apache-tomcat-9.0.56/bin/shutdown.sh
                    
                    ssh ec2-user@13.235.247.217 /home/ec2-user/apache-tomcat-9.0.56/bin/startup.sh
                
                """
            }
        }

    }
}
