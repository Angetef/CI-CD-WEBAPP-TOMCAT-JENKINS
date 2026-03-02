pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Angetef/CI-CD-WEBAPP-TOMCAT-JENKINS.git'
            }
        }

        stage('Build Project') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                bat '''
                copy /Y target\\monwebapp.war "C:\\tomcat\\apache-tomcat-10.1.52-windows-x64\\apache-tomcat-10.1.52\\webapps"
                '''
            }
        }
    }

    post {
        success {
            echo 'Déploiement réussi sur Tomcat'
        }
        failure {
            echo 'Pipeline échoué'
        }
    }
}
