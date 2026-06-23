pipeline {
agent any

triggers {
      cron('H/2 * * * *')
}
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
      }
}
