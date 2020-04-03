pipeline {
  agent any
  stages {
    stage('Parallel execution') {
      parallel {
        stage('Say Hello') {
          steps {
            sh 'echo "hello world"'
          }
        }

        stage('build app') {
          agent {
            docker {
              image 'gradle:jdk11'
            }

          }
          steps {
            sh '''#! /bin/bash
gradle clean shadowjar -p app
'''
            archiveArtifacts 'app/build/libs/'
          }
        }

      }
    }

  }
}