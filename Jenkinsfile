pipeline {   
    agent any
    parameters{
       choices(name:"VERSION" , choices:['1.1.0'] ,descreption:'')
       booleanParam(name: 'executeTests', defaultValue: true, description:'')
    }
    stages {
       stage("build") {
            steps {
                    echo "Building the application...."
            }
        }
        stage("test") {
            when{
                expression{
                    params.executeTests
                }
            }
            steps {
                    echo "Testing the application...."
            }
        }
        stage("deploy") {
            steps {
                    echo "Deploying the application...."
                    echo "Deploying version ${params.version}"
            }
        }               
    }
} 
