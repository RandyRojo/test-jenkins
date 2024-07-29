pipeline {
    agent any
    stages {
        stage('Clear WorkSpace') {
            steps {
                script {
                    sh "rm -rf ./*"
                }
            }
        }
        stage('Git Clone') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'XID-RandyRojo', usernameVariable: 'XID_GITHUB_USER', passwordVariable: 'XID_GITHUB_PASSWORD' )]) {
                    script {
                        sh "git clone https://${XID_GITHUB_USER}:'$XID_GITHUB_PASSWORD'@github.com/RandyRojo/test-jenkins"
                    }
                }
            }
        }
        stage('trigger job') {
            steps {
                script {
                    build job: 'quinto-pipeline', parameters: [
                        string(name: 'NOMBRE_PIPELINE', value: "$JOB_NAME"),
                        string(name: 'ID_JOB', value: "$BUILD_ID")
                    ]
                }
            }
        }
    }
}