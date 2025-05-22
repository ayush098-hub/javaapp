// node{
// stage('checkout'){
// checkout scm
// }
// stage('build'){
// def mvhome= tool name: 'mvn', type: 'maven'
// sh "${mvhome}/bin/mvn package"
// }
// }

pipeline {
    agent any

    environment {
        MAVEN_HOME = '/opt/apache-maven-3.9.9'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage("Package"){
            steps{
            
            sh "${MAVEN_HOME}/bin/mvn package"
        }
    }
         stage("build & SonarQube analysis") {
            steps {
              withSonarQubeEnv('SonarQube') {
                sh "${MAVEN_HOME}/bin/mvn clean package sonar:sonar"
              }
            }
    }
}
