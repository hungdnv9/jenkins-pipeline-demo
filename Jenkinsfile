pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image: 'python:2-apline'
                }
            }
            steps {
                sh 'python -m py_compile sources/calc.py'
                stash(name:'compile_result', includes: 'sources/*.py')
            }
        }
    }
}