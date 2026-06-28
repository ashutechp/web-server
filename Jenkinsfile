pipeline {
agent{      
    node { label 'ansible'}     
  }

    stages {
        stage('Checkout Code') {
            steps {
                // Assuming you have your Ansible playbook in a SCM like Git
                checkout scm
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                ansiblePlaybook(
                    credentialsId: 'ansible-ssh',
                    inventory: '/home/student/ansible/inventory',
                    playbook: '/home/student/ansible/myplaybook.yml'
                )
            }
        }
    }

    post {
        always {
            // Archive the Ansible playbook execution logs
            echo 'Playbook executed always successfully!'
        }
        success {
           // Notify success
            echo 'Playbook executed successfully!'
        }
        failure {
          // Notify failure
            echo 'Playbook execution failed!'
        }
    }
}
