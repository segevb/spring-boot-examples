pipeline {
  agent any
  stages {
    stage('Checkout code') {
      steps {
        git(url: 'https://github.com/segevb/spring-boot-examples.git', branch: 'segev_sol', changelog: true)
      }
    }

  }
}