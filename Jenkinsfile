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
          stage('Sonar analysis'){
              environment{
                  scannerHome = tool 'sonar_scanner'
              }
              steps {
                    withSonarQubEnv('sonar_local'){
                        bat "${scannerHome}/bin/sonar-scanner -e -Dsonar.projectKey=deployback -Dsonar.host.url=http://localhost:9000 -Dsonar.login=849e9cadd301bd28751e2fe723a2e145851c01bb -Dsonar.java.binaries=target"
                    }
            }
        }
    }
}

