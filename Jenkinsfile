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
                        sh 'node --version'
                        echo 'run coverage tests...'
                    }
                }
                stage('Test end to end') {
                    steps {
                        docker.image('postgres:9.4.1').withRun('-e "POSTGRES_USER=root" -p 5432:5432') { c ->
                            /* Wait until mysql service is up */
                            sh 'while ! nc -z localhost 5432; do sleep 1; done; echo "Postgres Server loaded"'
                            /* Run some tests which require MySQL */
                            echo 'run end to end tests...'
                        }         
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