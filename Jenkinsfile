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
                    withSonarQubeEnv('sonar_local'){
                        // Use a configured Java 11 or 17 tool installation
                        withEnv(['SONAR_SCANNER_OPTS=--add-opens=java.base/java.lang=ALL-UNNAMED']) {
                            sh 'sonar-scanner'
                        }
                        bat "${scannerHome}/bin/sonar-scanner -e -Dsonar.projectKey=deployback -Dsonar.host.url=http://localhost:9000 -Dsonar.login=849e9cadd301bd28751e2fe723a2e145851c01bb -Dsonar.java.binaries=target"
                    }
            }
        }
    }
}

