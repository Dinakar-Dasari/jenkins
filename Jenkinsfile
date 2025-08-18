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
                echo "Hello guru..!"
            }
        }
    }

    post { 
    always { 
        echo 'I will always say Hello again!'
        deleteDir()
    }
}