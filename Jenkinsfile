#!/user/bin/env groovy

library identifier: "jenkins-shared-library@master", retriever: modernSCM(
    [$class: 'GitSCMSource',
     remote: 'https://github.com/krish02416/jenkins-shared-library.git',
     credentialsId: 'git-credentials'])

def gv

pipeline {   
    agent any
    tools {
        maven 'maven-3.9'
    }
    stages {
        stage("init") {
            steps {
                script{
                   gv = load "script.groovy"
                }
            }
        }
       
       stage("build jar") {
            steps {
                script{
                     buildJar()
                }
            }
        }
        stage("build and push image") {
            steps {
                script{
                    buildImage 'harikrishnan20010616/demo-app:jma-3.0'
                    dockerLogin()
                    dockerPush 'harikrishnan20010616/demo-app:jma-3.0'

                }
            }
        }
        stage("deploy") {
            steps {
                script{
                   gv.deployApp()
                }
            }
        }               
    }
} 
