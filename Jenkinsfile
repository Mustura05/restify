pipeline {
    agent any

    stages {
        stage('Source') {
            steps {
                echo 'Pulling from GitLab'
            }
        }
        stage('Special Job') {
            when {
                branch 'special'
            }
            steps {
                echo '============Executing special steps........==========='
            }
        }
        stage('Build') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
            }
            steps {
                echo 'Start docker build'
                sh '''
                ls
                docker ps
                docker images
                docker build -t backend .
                docker images
                '''
            }
        }
    }
}
