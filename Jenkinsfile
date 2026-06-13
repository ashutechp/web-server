pipeline {
    agent: any
    environment {
        LINUX = 'redhat'
    }
    parameters {
     string(name: "person", defaultValue: "Ashutosh Pandey", description: "How are you?")
    }

    stages {
    stage('run linux command'){
        steps{
           sh 'date'
        }
    }

    stage('Check parameters'){
        steps {
            sh 'echo $person'
        }
    }
    }
}
