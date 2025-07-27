echo "Hello World"
pipeline {
    agent any
    stages{
        stage("Checkout"){
            steps{
                git branch:'main', url:'https://github.com/UshaNadarajan/spring-petclinic.git'
            }
        }
        stage("Build"){
            steps{
                bat 'mvnw.cmd package'
            }
        }
        stage("Capture"){
            steps{
                archiveArtifacts '**/target/*.jar'
                jacoco()
                junit '**/target/surefire-reports/TEST*.xml'
            }
        }
    }
    post{
        always{
            bat "echo Pipeline ran"
        }
    }
}