pipeline {
    agent any

    tools {
        maven "maven 3.9.11"
        jdk "JDK17"
    }

    stages {
        stage('SCM1') {
            steps {
                git branch: 'main', url: 'https://github.com/Venkiemc/Jenkins-demo-pipelines.git'
            }
        }

        stage('Build and Unit Test') {
            steps {
                bat 'mvn clean package'  // This will generate the JAR and run tests
            }
        }

        stage('Checkstyle Analysis') {
            steps {
                bat 'mvn checkstyle:checkstyle'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Now Archiving it...'
                archiveArtifacts artifacts: '**/target/*.jar'  // Archives the JAR file
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
