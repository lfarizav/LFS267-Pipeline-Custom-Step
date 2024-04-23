@Library('shared-library') _
pipeline {
  agent none
  stages {
    stage('Maven Build') {
      parallel {
        stage('Build JDK 21') {
          agent {
            node {
              label 'jdk21'
            }
          }
          steps {
            sh './jenkins/build.sh'
          }
          post {
            success {
              stash(name: 'Java 21', includes: 'target/**')
            }
          }
        }
        stage('Build JDK 17') {
          agent {
            node {
              label 'jdk17'
            }
          }
          steps {
            sh './jenkins/build.sh'
          }
          post {
            success {
             stash(name: 'Java 17', includes: 'target/**')
            }
          }
        }
      }
    }
  }
}
