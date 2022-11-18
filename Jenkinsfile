pipeline {

    agent {
    label 'Slave1'
    }

    stages {

        stage ('code') {
            steps{
                 git branch: 'main', credentialsId: 'github', url: 'https://github.com/devopsuniv/maven_project.git'
	            }
            }
         stage ('build') {
            steps{
                 bat 'mvn clean verify'
	            }
            }
	    stage ('Artifacts') {
		    steps {
		   archiveArtifacts artifacts: '**/*.war', followSymlinks: false
		    }
	    }
        stage ('deploy') {
          steps{
            deploy adapters: [tomcat9(credentialsId: '45a4486f-4acd-4fb0-9423-83b7f98c8a63', path: '', url: 'http://localhost:9090/')], contextPath: 'jenkinsdeclarative', war: '**/*.war'
	        }
        }
    }
}
