pipeline {
    agent { node { label 'AGENT-1' } }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }

1   post { 
        always { 
            echo 'I will always run whether job is success or not'
        }
        success { 
            echo 'I will run only job is success'
        }
        failure { 
            echo 'I will run when failure'
        }
    }

}