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
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage("Package"){
            steps{
            mvhome= tool name: 'mvn', type: 'maven'
            sh "${mvhome}/bin/mvn package"
        }
    }
    }
}
