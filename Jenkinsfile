

pipeline {
    agent any
  toold {
    maven 'Maven'
  }
    stages {
        
        stage("build jar") {
            steps {
                script {
                   echo "building the application..."
    sh 'mvn package'
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    echo "building the docker image..."
    withCredentials([usernamePassword(credentialsId: 'Docker_hub', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
        sh 'docker build -t mohamedayad10/Docker-Demo-App:2.0 .'
        sh "echo $PASS | docker login -u $USER --password-stdin"
        sh 'docker push mohamedayad10/Docker-Demo-App:2.0'
    }
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                        echo 'deploying the application...'

                }
            }
        }
    }   
}
