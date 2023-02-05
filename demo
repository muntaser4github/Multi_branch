pipeline {
    agent any 
/* parameters {
  string(name: 'name', description: 'devopsdeepdive')
} */
     stages {
        stage('Checkout') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github_cred', url: 'https://github.com/devopsdeepdive/teavm-maven-webapp.git']]]) 
            }
        }
        stage('Build') { 
            steps {
                sh 'mvn compile'
		    sleep time: 2, unit: 'MINUTES'
            }
        }
        stage('Test') { 
            steps {
               sh 'mvn test' 
            }
        }
		 stage('package') { 
            steps {
               sh 'mvn package' 
            }
        }
    }
}
