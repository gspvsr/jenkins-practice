pipeline {
    agent { node { label 'Agent-1' } }

    options {
        timeout(time: 1, unit: 'HOURS')
    }

    environment {
        USER = 'gsp'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
              sh '''
                ls -ltr
                pwd
                echo "hello-from GITHUB push webhook event santh prakash"
                printenv
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
