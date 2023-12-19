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
            emailext recipientProviders: [developers(), requestor()]
        }
    }
}
