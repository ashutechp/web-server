pipeline {
agent any


stages {

      stage("Parallel Tasks"){
            parallel { 
                  stage("parallel 1") {
                        steps{
                             echo "First Job"
                            }
                      }
                  stage("parallel 2") {
                        steps{
                              sh 'date'
                             }
                      }
                   } 
            }
      }
      post{
            always {
                  echo 'This code always execute'
            }
            success{
                  echo 'This code success execute'
            }
            unstable {
                  echo 'This code unstable execute'
            }
            failure {
                  echo 'This code failure execute'
            }
      }
}
