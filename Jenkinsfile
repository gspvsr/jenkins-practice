pipeline {
    agent { node { label 'Agent-1' } }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh '''
                ls -ltr
                pwd
                echo "hello-from GITHUB push webhook event gsp"
                '''
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
    }

    post { 
        always { 
            echo 'I will always run whether the job is a success or not'
        }
        success { 
            echo 'I will run only when the job is a success'
        }
        failure { 
            echo 'I will run when there is a failure'
        }
    }
}
