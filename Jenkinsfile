pipeline {
    agent any
    tools {
        maven 'Apache Maven 3.6.3'
    }
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
            }
        }
        stage('Upload War To Nexus'){
            steps{
                    nexusArtifactUploader artifacts: [
                        [
                            artifactId: 'simple-app', 
                            classifier: '', 
                            file: '/var/lib/jenkins/workspace/nexus-upload/target/simple-app-3.0.0-SNAPSHOT.war', 
                            type: 'war'
                        ]
                    ], 
                    credentialsId: 'nexus', 
                    groupId: 'in.javahome', 
                    nexusUrl: '3.137.164.105:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'http://3.137.164.105:8081/repository/bhanu-test-release/', 
                    version: '1.0.0'
            }
        }
    }
}
