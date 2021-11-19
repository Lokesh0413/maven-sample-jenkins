pipeline{
    agent any
    environment {
        PATH = "$PATH:/usr/local/apache-maven/apache-maven-3.8.3"
    }
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/Lokesh0413/maven-sample-jenkins.git'
            }
         }        
       stage('Build'){
            steps{
                sh 'mvn clean package'
            }
         }
        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('sonarqube-8.9.3') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn sonar:sonar"
    }
        }
        }
       
    }
}
