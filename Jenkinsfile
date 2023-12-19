pipeline {
    agent {
        label 'master'
    }
    stages {
        stage("test") {
            steps {
                script {
                    println("hello world4")
                    emailext body: 'hello world4', subject: 'test build', recipientProviders: [developers(), requestor()]
                }
            }
        }
    }
}
