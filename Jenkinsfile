echo "Hello World"
pipeline {
    agent any
    stages{
        stage("Build"){
            steps{
                bat 'mvnw.cmd package'
                releasenotes()
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
