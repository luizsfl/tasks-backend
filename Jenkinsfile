pipeline {
    agent any
    stages {
        stage('just test'){
            steps {
                bat 'mvn clean package -DskipTests=true'
            }
        }
    }
}
