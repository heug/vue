pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                checkout scm
                echo 'Installing dependencies...'
                stash
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