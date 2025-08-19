pipeline {
    agent { label "agent-1"}
    environment {
        appVersion = " "
        REGION = "us-east-1"
        ACC_ID = "127218179061"
        PROJECT = "roboshop"
        COMPONENT = "catalogue"

    }
    // Build
    stages{
        stage("build"){
            steps{
                script {
                   def packageJson = readJSON file: 'package.json'     
                   appVersion = packageJson.version
                   echo "Package version: ${appVersion}"
                }
            }
        stage("install dependencies")
            steps{
                script{
                    sh """
                    npm install
                """
                }
            }    
        }
        stage("Unit test"){
            steps{
                echo "unit test"
            }
        }
        stage("Docker Build"){
            steps{
                script{
                    withAWS(credentials: 'aws-cred', region: 'us-east-1') {
                        sh """
                                aws ecr get-login-password --region ${REGION} | docker login --username AWS --password-stdin ${ACC_ID}.dkr.ecr.us-east-1.amazonaws.com
                                docker build -t ${ACC_ID}.dkr.ecr.us-east-1.amazonaws.com/${PROJECT}/${COMPONENT}:${appVersion} .
                                docker push ${ACC_ID}.dkr.ecr.us-east-1.amazonaws.com/${PROJECT}/${COMPONENT}:${appVersion}
                        """
                }      
                }

            }
        }

        post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        success { 
            echo 'Hello Success'
        }
        failure { 
            echo 'Hello Failure'
        }
    }

    }
}