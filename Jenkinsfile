pipeline {
    agent any

    stages {

        stage('Cloner le code') {
            steps {
                echo 'Clonage du projet...'
                checkout scm
            }
        }

        stage('Build avec Maven') {
            steps {
                echo 'Compilation du projet...'
                bat 'mvn clean package'
            }
        }

        stage('Déploiement sur Tomcat') {
            steps {
                echo 'Déploiement vers Tomcat...'
                bat '''
                copy /Y target\\monwebapp.war C:\\tomcat\\apache-tomcat-10.1.52-windows-x64\\apache-tomcat-10.1.52\\webapps
                '''
            }
        }

    }

    post {
        success {
            echo 'Déploiement réussi 🚀'
        }
        failure {
            echo 'Échec du pipeline ❌'
        }
    }
}
