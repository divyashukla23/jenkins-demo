// pipeline {
//     agent any

//     stages {
//         stage('Execute shell script') {
//             steps {
//                script{
//                 sh './script.sh'
//                }
//             }
//         }
//     }
// }
pipeline {
    agent any
    environment {
        EMAIL_RECIPIENT = 'divyashukla20993@gmail.com'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the project...'
                }
            }
        }
    }
    post {
        success {
            emailext(
                to: "${EMAIL_RECIPIENT}",
                subject: "Build Successful: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The build was successful. You can view it at ${env.BUILD_URL}"
            )
        }
        failure {
            emailext(
                to: "${EMAIL_RECIPIENT}",
                subject: "Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The build has failed. You can view it at ${env.BUILD_URL}"
            )
        }
    }
}

