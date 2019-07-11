pipeline {
    agent {
        docker {
            image 'node:6.10.0'
        }
    }

    stages {
        stage('Build') {
            steps {
                checkout scm
                echo 'Installing dependencies...'
                stash name: 'app'
            }
        }
        stage('Run Tests') {
            parallel {
                stage('Test lint-flow-types') {
                    steps {
                        unstash 'app'
                        sh 'ls -al'
                        echo 'run linting tests..'
                    }
                }
                stage('Test coverage') {
                    steps {
                        echo 'run coverage tests...'
                    }
                }
                stage('Test end to end') {
                    steps {
                        echo 'run end to end tests...'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}