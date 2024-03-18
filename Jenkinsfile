pipeline {
    agent any
    tools {
        maven 'maven'
    }
    
    stages {
        
        stage('Build'){
            steps {
                bat 'call mvn clean install package'
            }
        }
        
        stage('Test'){
            steps {
                echo 'Testing--------------'
            }
        }
        //Publish the Artifacts to Nexus
        stage('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.8.war', type: 'war']], credentialsId: 'c044a60f-917d-4733-aee7-bfcc41e91748', groupId: 'com.vinaysdevopslab', nexusUrl: '369a-103-146-0-201.ngrok-free.app', nexusVersion: 'nexus2', protocol: 'https', repository: 'MyLabDemo-SNAPSHOT', version: '0.0.8'
            }
        }
        
        stage('Deploy'){
            steps {
                echo 'Deploying------------'
            }
        }
    }
}
