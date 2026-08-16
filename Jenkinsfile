pipeline {
    agent any
    tools {
        jdk 'JDK_17'
    }
    stages {
        stage('Build & Test') {
            steps {
                bat 'mvn clean verify'
            }
        }
        stage('Sonar analysis') {
            steps {
                withSonarQubeEnv('sonar_local') {
                    // O plugin do Maven lê automaticamente as fontes e o bytecode do Java 17
                    bat 'mvn sonar:sonar -Dsonar.projectKey=deployback'
                }
            }
        }
    }
}
