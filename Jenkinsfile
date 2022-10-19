pipeline {
         agent any
         stages {
                 stage('Build') {
                 steps {
                     echo 'Hi, stage . Starting to build the App.'
                 }
                 }
                 stage('GitHub Jenkins Ant Docker Build') {
                 steps {
                     git 'https://github.com/nijaouiOumaima/CI-CD-pipeline-sample-app.git'
                     sh 'ant clean compile test package war'
                 }
                 }
                 stage('Test') {
                 steps {
                    input('Do you want to proceed?')
                 }
                 }
                 stage('Deploy') {
                 parallel { 
                            stage('Deploy start ') {
                           steps {
                                echo "Start the deploy .."
                           } 
                           }
                            stage('Deploying now') {
                            agent {
                                    docker {
                                            reuseNode true
                                            image ‘nginx’
                                           }
                                    }
                            
                              steps {
                                echo "Docker Created"
                              }
                           }
                           }
                           }
                 stage('Prod') {
                     steps {
                                echo "App is Prod Ready"
                              }
                 
              }
}
}
