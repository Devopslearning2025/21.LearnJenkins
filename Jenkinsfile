pipeline {
    agent {
        label 'Agent-1'
    }
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['Dev', 'QA', 'Prod'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    environment {
        DEPLOY_TO = 'production'
        GREETING  = 'Good Monring"'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo this is build'
            }
        }
        stage('Test') {
            steps {
                sh 'echo this is test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'env'                
               // sh 'echo this is deploy'
               echo "this is deploy"
            }
        }
        stage('print parameeters') {
            steps{
                echo "Helloo: ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.TOGGLE}"
                echo "Choice: ${params.CHOICE}"
//                echo "Password: ${params.PASSWORD}"
                echo "Trigger test again"
                //error 'some failure'
            }
        }        
    }
    post { 
       always {
            echo 'I will always say Hello again!'
        }
        success {
            echo 'i will run the pipeline is success'
        }
        failure {
            echo 'i will run when pipeline is failure'
        }
    }
}