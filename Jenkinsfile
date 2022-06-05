pipeline {
    agent any
    stages {
        stage('Deploy stack from docker-compose file.') {
            steps {
                sh 'docker stack deploy -c docker-compose.yml serviceconstraints'
            }
        }
        stage('Approval to kill'){
            steps {
                input "Can we stop and remove the stack?"
                sh 'docker stack rm serviceconstraints'
            }
        }
    }
    post('If fail, stop and remove containers.'){
        failure {
            sh 'docker stack rm serviceconstraints'
        }
    }
}
