pipeline {
     agent any
     stages {
        stage("Build") {
            steps {
                sh "docker build -t react-jenkins-ansible ."
                sh "sudo npm install"
                sh "sudo npm run build"             
            }
        }
        stage("Deploy") {
            steps {
                sh "ansiblePlaybook credentialsId: 'ansible-ssh-key', inventory: 'inventory.ini', playbook: 'ansible-build-docker-remote.yml'"
                sh "sudo rm -rf /var/www/reactapp"
                sh "sudo cp -r ${WORKSPACE}/build/ /var/www/reactapp/"
            }
        }
    }
}
