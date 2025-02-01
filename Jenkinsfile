pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
               sh 'which pipenv'
               sh 'pipenv --python python3 sync'
            }
        }
        stage('Test') {
            steps {
               sh 'pipenv run pytest'
            }
        }
        stage('Package') {
            when{
                anyOf{ branch "master" ; branch 'release' }
            }
            steps {
               sh 'zip -r sbdl.zip lib'
            }
        }
    }
}
