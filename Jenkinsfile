pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'python:2-alpine'
                }
            }
            steps {
                sh 'python -m py_compile sources/calc.py'
                stash(name:'compile_result', includes: 'sources/*.py')
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'qnib/pytest'
                }
            }
            steps {
                sh 'py.test --junit-xml test-reports/result.xml sources/test_calc.py'
            }
            post {
                always {
                    junit 'test-reports/result.xml'
                }
            }
        }
    }
}