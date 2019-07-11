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
        // stage('Test') {
        //     steps {
        //         echo 'Testing..'
        //     }
        // }
        // stage('Deploy') {
        //     steps {
        //         echo 'Deploying....'
        //     }
        // }
    }
}