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
  stage('TomcatDeply') {
    steps {
    sshagent(['tomcat']) {
sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/maven-web-project-multi-branches/target/teavm-maven-webapp-1.0-SNAPSHOT.war ubuntu@172.31.0.57:/var/lib/tomcat9/webapps/'
}
    }
  }
  stage('Notification')
    steps{
      slackSend channel: 'devopsdeepdive_batch13', message: 'Build succussed  '
    }
  }
}

}

