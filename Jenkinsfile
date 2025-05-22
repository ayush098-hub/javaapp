node{
stage('checkout'){
checkout scm
}
stage('build'){
def mvhome= tool name: 'mvn', type: 'maven'
sh '${mvhome}/bin/mvn package'
}
}
