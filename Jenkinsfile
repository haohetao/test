pipeline {
    agent any
    stages {
        stage("test") {
            steps {
                script {
                    println("hello world4")
                    sh 'env'
                }
            }
        }
    }
    post {
        always {
            emailext subject: "${currentBuild.currentResult}: Job - ${env.JOB_NAME}#${env.BUILD_NUMBER}",
            body: """<p>${currentBuild.currentResult}: ${env.JOB_NAME}#${env.BUILD_NUMBER}:</p><p>Check console output at
            <a href='${env.BUILD_URL}'>${env.JOB_NAME}#${env.BUILD_NUMBER}</a>
            </p>""",
            recipientProviders: [developers(), requestor()]
        }
    }
}