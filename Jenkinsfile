pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage("git"){
            steps{
                git 'https://github.com/Manojkcsit/hello-world.git'
                
            }
        }
        stage("build code"){
            steps{
                sh "mvn clean package"
            }
        }
        stage("deploy code"){
            steps{
                sshagent(['pipe_ssh']) {
                   sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ubuntu@107.23.49.48:/opt/tomcat/webapps"
                }
            }
        }
    }
}
