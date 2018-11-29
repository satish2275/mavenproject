#! /bin/g
pipeline 
  {
      agent any
      
      tools {
        maven 'Maven'
       }
      stages {
          stage('SCM') {
              steps {
                  git 'https://github.com/satish2275/mavenproject'
                  echo 'Source code downloaded from scm'
                  
              }
          }
          
          stage('Build') {
              steps {
                  sh 'mvn clean' 
                  echo 'package building'
              }
          }
          
          stage('QA') {
              steps {
                  echo 'Deploying to testing environment '
              }
          }
          
          stage('Deploy') {
              when {
                  expression {
                      currentBuild.result == 'FAILURE'
                  }
              }
                  steps {
                      echo 'Build successful and deployment underprogress'
                  }
                  
              }
              
          
      }
  }peline 
