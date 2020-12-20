pipeline {
    agent any
	tools {
        maven 'maven'
        jdk 'jdk1.8'
    }
	
    stages{
	    stage ('Initialize') {
            steps {
                sh """
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                """
            }
        }
	    stage('git-checkout'){
            steps{
                 git credentialsId: 'git', url: 'https://github.com/sumanthdevops/mavenproject.git'
            }
        }
        stage('Build'){
            steps{
                 sh 'mvn package'
                 
            }
        }
        stage('Upload War To Nexus'){
            steps{
                
                    nexusArtifactUploader artifacts: [
					     [
					       artifactId: 'devops3',
					       classifier: '', 
						   file: 'target/devops3.war', 
					       type: 'war'
				        ]
				], 
				credentialsId: 'nexus',
				groupId: 'org.tinygroup', 
				nexusUrl: '13.233.130.173:8081', 
				nexusVersion: 'nexus3', 
				protocol: 'http', 
				repository: 'simpleapp', 
				version: '1.0'
             }
        }
    }
 }
 	
