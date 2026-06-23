pipeline {
    
agent any

stages {
    
        stage("Parallel Tasks"){
           
          
                parrallel {
                   
                        stage("One"){
                             steps{
                                 echo "First Job"
                             }
                        }
                        stage("Two"){
                             steps{
                                 echo "Second Job"
                             }
                        }
                        
                    
                    
                }
           
        }

    }
