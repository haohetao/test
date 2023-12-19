pipeline {
    agent any
    stages {
        stage("test") {
            steps {
                script {
                    println("hello world4")
                }
            }
        }
    }
    post {
        always {
            emailext subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
            body: """<p>FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p><p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
            recipientProviders: [developers(), requestor()]
        }
    }
}
