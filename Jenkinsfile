pipeline {
    agent any
    tools {
        maven 'Maven-3.8.4'  // Remplacez par la version de Maven installée dans Jenkins
        jdk 'jdk-11'         // Remplacez par la version de JDK installée dans Jenkins
    }
    triggers {
        githubPush()  // Déclenche le pipeline à chaque push sur GitHub
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/JOUDASHY/demo-jenkins.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }
    post {
        success {
            echo 'Build réussi !'
        }
        failure {
            echo 'Build échoué !'
        }
    }
}
