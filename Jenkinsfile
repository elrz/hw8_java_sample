pipeline{
    agent any

    tools {
        maven 'maven 3.8.6'
        git 'Default'
    }

    parameters {
        string (name: 'TAG', defaulValue: "latest")
        booleanParam(name: 'SKIP_TEST', defaultValue: false)
        booleanParam(name: 'SKIP_PUBLISH_IMAGE' defaultValue: false)
        
    }

    stages {
        stage ('Build'){
            steps{
                sh 'mvn clean packege'
                
            }
        }
        stages ('Run test'){
            steps{
                sh 'mvn clean test'
            }
        }

        stages ('Docker build'){
            steps{

                sh 'uname -a'
            }
        }
        stages ('Docker push'){
            steps{

                sh 'pwd'
            }
        }
    }


}
