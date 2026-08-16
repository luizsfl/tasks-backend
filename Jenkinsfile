pipeline {
    agent any
    stages {
        stage('build backend'){
            steps {
                bat 'mvn clean package -DskipTests=true'
            }
        }
        stage(' Junit Testes'){
            steps {
                bat 'mvn test'
            }
        }
    }
}
