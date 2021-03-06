

pipeline {
    agent any
    
    stages {
         stage ('Clone') {
            steps {
                git branch: 'master', url: "https://github.com/Srinu7358/spring-petclinic.git"
            }
         }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            }
        stage('Junit') {
            steps {
                junit 'target/surefire-reports/*.xml'
            }
            }
            stage('archival') {
            steps {
                archiveArtifacts 'target/*.jar'
            }
            }
        stage ('Artifactory configuration') {
            steps {
             rtServer (
    id: 'ARTIFACTORY_SERVER',
    url: 'http://54.185.210.104:8081/artifactory/',
    username: 'admin',
    password: 'password',
    bypassProxy: true
          )
       
}
        }  
    }   
}


        
