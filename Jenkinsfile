pipeline 
  {
      agent {
              docker {
                     image 'maven:3-alpine'
                     args '-v $HOME/.m2:/root/.m2'
                     }
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
                  sh 'mvn clean package' 
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
}
