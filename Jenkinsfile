pipeline {
    agent any
    parameters {
        string(name: 'APP_VERSION', defaultValue: '1.1.0', description: 'App current version')
        text(name: 'AUTHOR', defaultValue: 'hungdnv', description: 'Something is better than nothin')
        boolean(name: 'doDeploy', defaultValue: false, description: 'If true do deploy')
        choice(name: 'DEPLOY_EVN', choice: ['prod', 'staging', 'dev'], description: '')
        password(name: 'AWS_SECRET', defaultValue: 'canyouseeme' ,description: 'AWS secret key')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building step ...'
                sh "app version is ${params.APP_VERSION}"
                sh "author ${params.AUTHOR}"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing steps ...'
                echo 'What is the environment choice?'
                sh "Result: ${params.DEPLOY_EVN}"
            }
        }
        stage('Deploy') {
            when {
                expression {
                    params.doDeploy == true
                }
            }
            steps {
                echo 'Deploying steps ....'
            }
        }        
    }
}
