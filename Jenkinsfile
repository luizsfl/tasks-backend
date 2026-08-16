pipeline {
    agent any
    tools {
        // O nome deve ser EXATAMENTE o mesmo cadastrado nas Ferramentas
        jdk 'JDK_17'
    }
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
                        withEnv(['SONAR_SCANNER_OPTS=--add-opens=java.base/java.lang=ALL-UNNAMED']) {
                        script {
                            bat "${scannerHome}\\bin\\sonar-scanner.bat -Dsonar.projectKey=meu-projeto -Dsonar.sources=."
                        }
                    }
                        bat "${scannerHome}/bin/sonar-scanner -e -Dsonar.projectKey=deployback -Dsonar.host.url=http://localhost:9000 -Dsonar.login=849e9cadd301bd28751e2fe723a2e145851c01bb -Dsonar.java.binaries=target"
                    }
            }
        }
    }
}

