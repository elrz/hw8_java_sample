pipeline{
    agent any

    tools {
        maven 'maven 3.8.6'
    }

    triggers {
        cron ' 0 5 * * *'
    }


    options {
        disableConcurrentBuilds()
        timestamps()
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
            when {
                expression{
                    return params.SKIP_TEST == false;
                }
            }
            steps{
                sh 'mvn clean test'
            }
        }

        stage ('Docker build'){
           
            steps{

                sh 'docker build -t routeg/java-sample:${TAG} .'
            }
        }
        stage ('Docker push'){
             when {
                expression {
                    return params.SKIP_PUBLISH_IMAGE == false;
                }
            }

            
            steps{
                withDockerRegistry(url: 'https://index.docker.io/v1/', credentialsId: 'dockerhub-token') {
                    sh 'docker push routeg/java-sample:${TAG}'
                }
            }
        }
    }


}
