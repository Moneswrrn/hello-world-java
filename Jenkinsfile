pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { git branch: 'master', url: 'https://github.com/Moneswrrn/hello-world-java.git' }
        }
        stage('Build'){
            steps { bat 'start gradlew build' }
        }
        stage('Test'){
            steps { bat 'start gradlew test' }
        }
        stage('Deploy'){
            steps {
                powershell 'java -jar build/libs/hello-world-java-V1.jar'
            }
        }
    }
}

post {
    always {
        echo 'Cleaning up workspace'
        deleteDir()
    }
    success {
        echo 'Build succeeded!!!'

    }
    failure {
        echo 'Build failed!'
    }
}