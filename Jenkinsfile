pipeline {
    agent any

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
                        echo 'run linting tests..'
                    }.
                }
                stage('Test coverage') {
                    steps {
                        echo 'run coverage tests...'
                    }
                }
            }
        }
        // stage('Deploy') {
        //     steps {
        //         echo 'Deploying....'
        //     }
        // }
    }
}