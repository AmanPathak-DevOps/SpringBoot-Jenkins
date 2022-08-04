pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages{
        stage("Test"){
            steps{
                sh 'mvn test'
                echo "========executing A========"
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
            }
        }
        stage("Deploy-On-Test"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat9details', path: '', url: 'http://18.207.190.140:8080/')], contextPath: '/app', war: '**/*.war'
            }
        }
        stage("Deploy-On-Prod"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat9details', path: '', url: 'http://54.227.217.199:8080/')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
}
