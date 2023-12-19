pipeline {
    agent {
        label 'master'
    }
    stages {
        stage("test") {
            steps {
                script {
                    println("hello world2")
                    emailext body: 'Test Message', subject: 'Test Subject', recipientProviders: [developers(), requestor()]
                }
            }
        }
    }
}
