        
pipeline{
    agent any
    
    environment{
        PATH = "/opt/maven3/bin:$PATH"
    }
    stages{
        stage("Git Checkout"){
            steps{
                git branch: 'dev', credentialsId: 'karthik', url: 'https://github.com/Charykarthik/code.git'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                sh "mv target/*.war target/myweb.war"
            }
        }
        stage("deploy"){
            steps{
                  deploy adapters: [tomcat9(credentialsId: '9d8b480d-8752-4e32-b5e7-9ce5fb4e48b0', path: '', url: 'http://34.135.82.198:8080/')], contextPath: 'webapps', war: 'target/*.war'
                                       
            }
        }
    }
}
