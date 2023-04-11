pipeline {
     agent any
     stages {
        stage("Build") {
            steps {
                sh "docker build -t react-jenkins-ansible ."
                            
            }
        }
        stage("Deploy") {
            steps {
                sh "ansiblePlaybook credentialsId: 'ansible-ssh-key', inventory: 'inventory.ini', playbook: 'ansible-build-docker-remote.yml'"

            }
        }
    }
}
