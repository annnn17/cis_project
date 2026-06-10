pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Checkout Code') {
            steps {
                cleanWs()
                checkout scm
            }
        }

        stage('Docker Deploy') {
            steps {
                echo 'Restarting containers for project_06...'
                sh 'docker compose -p project_06 down'
                sh 'docker compose -p project_06 up -d --build'
            }
        }
    }
}
