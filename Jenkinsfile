// test2
env['test'] = 'a1'
def readEnv() {
    readYaml(file: "pipeline-env.yaml").each {
        key, value -> env[key] = value
    }
}
node() {
    //readEnv()
}
pipeline {
    agent any
    options { timestamps() }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    }
    stages {
        stage("test") {
            options { retry(3) }
            steps {
                script {
                    println("hello world4")
                    sh 'env'
                }
            }
        }
        stage('Example') {
            steps {
                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.TOGGLE}"
                echo "Choice: ${params.CHOICE}"
            }
        }
        stage('env') {
            steps {
                readEnv()
                echo "${test}"
            }
        }
    }
    post {
        always {
            emailext subject: "${currentBuild.currentResult}: Job - ${env.JOB_NAME}#${env.BUILD_NUMBER}",
            body: """<p>${currentBuild.currentResult}: ${env.JOB_NAME}#${env.BUILD_NUMBER}</p><p>Check console output at
            <a href='${env.BUILD_URL}'>${env.JOB_NAME}#${env.BUILD_NUMBER}</a>
            </p>""",
            recipientProviders: [developers(), requestor()]
        }
    }
}
