pipeline {
  agent any
  stages {
    stage('error') {
      steps {
        tool(type: 'MAVEN3.6', name: 'MAVEN3.6')
        tool(name: 'my-maven', type: 'MAVEN3.6')
      }
    }

    stage('Pull Github') {
      steps {
        git(url: 'ssh://git@github.com:wjfrelo/maven-build-pipeline.git', branch: 'main', credentialsId: 'wjfrelo', poll: true, changelog: true)
      }
    }

    stage('Build') {
      steps {
        sh 'sh \'mvn compile\''
      }
    }

    stage('Unit Test') {
      steps {
        sh 'sh \'mvn test\''
      }
    }

  }
}