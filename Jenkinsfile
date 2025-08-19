// pipeline {
//     agent { label "agent-11" }  ---> matching label will run this build

//     stages {   ---> it can have one or multiple stages
//         stage('Build') {   ---> stage 1
//             steps {    ---> it can have multiple steps
//                 echo 'Building..'
//             }
//         }
//         stage('Test') {
//             steps {
//                 echo 'Testing..'
//             }
//         }
//         stage('Deploy') {
//             steps {
//                 echo 'Deploying....'
//             }
//         }
//     }
// }



pipeline{
    agent {label "agent-11"}
    stages{
        stage('Dinakar'){
            steps {
                script {   // scripting So, this becomes scripting + declarative
                    sh 'pwd' // each command is a step --> step 1  
                    echo "hello"  // step 2
                }
            }
        }
    }

    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir() // --> this will delete the files in workspace directory in agent
        }
    }

}