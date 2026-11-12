pipeline {
    agent any
    environment  {
        PATH = "/opt/maven/bin:$PATH"
    }
    
    stages {

        stage("build") {
            steps {
                sh 'mvn clean package'
            }
         }
         
         stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'saidemy-sonar-scanner' 
            }

            steps {
                withSonarQubeenv('saidemy-sonarqube-server')
               
                    sh "${scannerHome}/bin/sonar-scanner"
                }
             } 
           }
        }
     
    
