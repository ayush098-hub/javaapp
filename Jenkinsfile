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
        
        stage("Package") {
            steps {
                sh "${MAVEN_HOME}/bin/mvn package"
            }
        }
        
        stage("Build & SonarQube Analysis") {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "${MAVEN_HOME}/bin/mvn clean package sonar:sonar"
                }
            }
        }
        
        // stage("Quality Gate") {
        //     steps {
        //         script {
        //             def qualitygate = waitForQualityGate()
        //             if (qualitygate.status != "OK") {
        //                 error "Pipeline aborted due to quality gate failure: ${qualitygate.status}"
        //             }
        //         }
        //     }
        // }

        stage("Deploy to tomcat"){
        steps{
            sh 'cp target/*.war /opt/apache-tomcat-9.0.105/webapps'
        }
        }
    }
}
