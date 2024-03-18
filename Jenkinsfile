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

        stage('Publish To Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.8.war', type: 'war']], credentialsId: '928fdfe5-fb6a-492a-a506-774288808d7d', groupId: 'com.vinaysdevopslab', nexusUrl: '369a-103-146-0-201.ngrok-free.app', nexusVersion: 'nexus3', protocol: 'https', repository: 'MyLabDemo-SNAPSHOT', version: '0.0.8'
            }
        }
        
        stage('Deploy'){
            steps {
                echo 'Deploying------------'
            }
        }
    }
}
