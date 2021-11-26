pipeline {
    agent any
    tools {
        maven 'Apache Maven 3.6.3'
    }
    options {
        buildDiscarder logRotator(daysToKeepStr: '5', numToKeepStr: '7')
    }
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
                 archiveArtifacts artifacts: 'target/*.war', onlyIfSuccessful: true
            }
        }
        stage('Upload War To Nexus'){
            steps{
                script{

                    def mavenPom = readMavenPom file: 'pom.xml'
                    def nexusRepoName = mavenPom.version.endsWith("SNAPSHOT") ? "simpleapp-snapshot" : "simpleapp-release"
                    nexusArtifactUploader artifacts: [
                        [
                            artifactId: 'simple-app', 
                            classifier: '', 
                            file: "target/simple-app-${mavenPom.version}.war", 
                            type: 'war'
                        ]
                    ], 
                    credentialsId: 'nexus3', 
                    groupId: 'in.javahome', 
                    nexusUrl: 'pipeline' {
    agent any
    tools {
        maven 'Apache Maven 3.6.3'
    }
    options {
        buildDiscarder logRotator(daysToKeepStr: '5', numToKeepStr: '7')
    }
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
                 archiveArtifacts artifacts: 'target/*.war', onlyIfSuccessful: true
            }
        }
        stage('Upload War To Nexus'){
            steps{
                script{

                    nexusArtifactUploader artifacts: [
                        [
                            artifactId: 'simple-app', 
                            classifier: '', 
                            file: 'target/simple-ap-1.0.0.war', 
                            type: 'war'
                        ]
                    ], 
                    credentialsId: 'nexus3', 
                    groupId: 'in.javahome', 
                    nexusUrl: '3.137.164.105', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'http://3.137.164.105:8081/#browse/browse:bhanu-test-release', 
                    version: '1.0.0'
                    }
            }
        }
    }
}, 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'http://3.137.164.105:8081/#browse/browse:bhanu-test-release', 
                    version: '1.0.0'
                    }
            }
        }
    }
}
