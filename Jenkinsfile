pipeline {
agent any
stages {
  stage('checkout') {
    steps {
      checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github_maven_account', url: 'https://github.com/muntaser4github/maven-web-project-multi-branches.git']])
    }
  }
stage('compile') {
    steps {
sh 'mvn compile'
    }
  }
  
  stage('package') {
    steps {
sh 'mvn package -Dmaven.test.skip=true'
    }
  }
  
}

}

