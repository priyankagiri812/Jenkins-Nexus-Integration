pipeline {
    agent any
    tools {
        maven 'maven'
    }
    
    environment{
        ArtifactID = readMavenpom().getartifactId()
        Version = readMavenpom().getversion()
        Name = readMavenpom().getname()
        GroupID = readMavenpom.getgroupId()
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
                nexusArtifactUploader artifacts: [
                    [artifactId: "${ArtifactID}", 
                    classifier: '', 
                    file: 'target/VinayDevOpsLab-0.0.1-SNAPSHOT.war', 
                    type: 'war']], 
                    credentialsId: '928fdfe5-fb6a-492a-a506-774288808d7d', 
                    groupId: "${GroupID}", 
                    nexusUrl: 'c2bb-103-146-0-201.ngrok-free.app', 
                    nexusVersion: 'nexus3', 
                    protocol: 'https', 
                    repository: 'MyLabDemo-SNAPSHOT', 
                    version: "${Version}"
            }
        }
       
        stage('Deploy'){
            steps {
                echo 'Deploying------------'
            }
        }
    }
}
