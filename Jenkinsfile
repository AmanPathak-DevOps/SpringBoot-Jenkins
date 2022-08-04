pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages{
        stage("Test"){
            steps{
                sh 'mvn test'
                slackSend channel: 'jenkins-notify', message: 'Job Started'
            }
            // post{
            //     always{
            //         echo "========always========"
            //     }
            //     success{
            //         echo "========A executed successfully========"
            //     }
            //     failure{
            //         echo "========A execution failed========"
            //     }
            // }
        }
        stage("Build"){
            steps{
                sh 'mvn package'
                slackSend channel: 'jenkins-notify', message: 'Build Started'
            }
        }
        stage("Deploy-On-Test"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat9details', path: '', url: 'http://18.207.190.140:8080/')], contextPath: '/app', war: '**/*.war'
                slackSend channel: 'jenkins-notify', message: 'Deployment on Test Started'
            }
        }
        stage("Deploy-On-Prod"){
            input {
                message "Shall We Continue?"
                ok "Yes! You can"
            }
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat9details', path: '', url: 'http://54.227.217.199:8080/')], contextPath: '/app', war: '**/*.war'
                slackSend channel: 'jenkins-notify', message: 'Deployment on Production Started'
            }
        }
    }
}
