pipeline {
     agent any
stages{
        stage('Code'){
            steps{
                git url: 'https://github.com/dasmaihar2017/react-app-jenkins-pipline.git', branch: 'master' 
            }
        }
     stages {
        stage('Build and test') {
            steps {
                 sh 'docker build -t react-jenkins-ansible .'
                 sh "sudo npm install"
                 sh "sudo npm run build"
                            
            }
        }
        stage("Deploy") {
            steps {
                sh "sudo rm -rf /var/www/reactapp"
                sh "sudo cp -r ${WORKSPACE}/build/ /var/www/reactapp/"
            }
        }
    }
}
