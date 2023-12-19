pipeline {
    agent {
        label 'master'
    }
    stages {
        stage("test") {
            steps {
                script {
                    println("hello world3")
                    emailext body: 'hello world3', subject: 'test build', recipientProviders: [developers(), requestor()]
                }
            }
        }
    }
}
