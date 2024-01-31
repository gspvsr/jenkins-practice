pipeline {
    agent { node { label 'Agent-1' } }

    options {
        timeout(time: 1, unit: 'HOURS')
    }

    triggers {
        cron('0 * * * *')
    }

    environment {
        USER = 'gsp'
    }

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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

        stage('Example') {
            environment {
                AUTH = credentials('ssh_auth')
            }
            steps {
                sh 'printenv'
            }
        }

        stage('Example1') {
            steps {
                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.TOGGLE}"
                echo "Choice: ${params.CHOICE}"
                echo "Password: ${params.PASSWORD}"
            }
        } 

        stage('Input') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }

            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
        stage('PROD DEploy'){
            when {
                environment name: 'USER' , value: 'sivakumar'
            }
            steps {
                echo "deploying to PROD"
            }
        }
        stage('Parallel Stage') {
            parallel {
                stage('Branch A') {
                    steps {
                        echo "On Branch A"
                        sh 'sleep 10'
                    }
                }
                stage('Branch B') {
                    steps {
                        echo "On Branch B"
                        sh 'sleep 10'
                    }
                }
                stage('Branch C') {
                    stages {
                        stage('Nested 1') {
                            steps {
                                echo "In stage Nested 1 within Branch C"
                                sh 'sleep 10'
                            }
                        }
                        stage('Nested 2') {
                            steps {
                                echo "In stage Nested 2 within Branch C"
                                sh 'sleep 10'
                            }
                        }
                    }
                }
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
