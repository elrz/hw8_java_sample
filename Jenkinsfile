pipeline{
    agent any

    tools {
        maven 'maven 3.8.6'
    }

    parameters {
        string (name: 'TAG', defaultValue: "latest")
        booleanParam(name: 'SKIP_TEST', defaultValue: false)
        booleanParam(name: 'SKIP_PUBLISH_IMAGE', defaultValue: false)
    }

    stages {
        // stage ('Build'){
        //     steps{
        //         sh 'mvn clean packege'
                
        //     }
        // }
        stage ('Run test'){
            steps{
                sh 'mvn clean test'
            }
        }

        stage ('Docker build'){
            steps{

                sh 'docker build -t java-sample:latest .'
            }
        }
        stage ('Docker push'){
            steps{

                sh 'pwd'
            }
        }
    }


}
