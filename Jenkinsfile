pipeline {
  agent {
    node {
      label 'centos7-nodejs'
    }

  }
  stages {
    stage('Checkout code') {
      steps {
        git(url: 'https://github.com/segevb/spring-boot-examples.git', branch: 'segev_sol', changelog: true)
      }
    }

    stage('Maven compile - {mvn build}') {
      steps {
        sh '''cd spring-boot-package-war
mvn compile'''
      }
    }

    stage('Test {mvn test}') {
      steps {
        sh '''cd spring-boot-package-war
mvn test'''
      }
    }

    stage('Increment pom file') {
      steps {
        sh '''cd spring-boot-package-war
mvn build-helper:parse-version versions:set -DnewVersion=0.0.1.$BUILD_ID-SNAPSHOT versions:commit
'''
      }
    }

    stage('Package Code') {
      steps {
        sh '''cd spring-boot-package-war
mvn clean package'''
      }
    }

  }
}