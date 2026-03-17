pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time: 10, unit: 'SECONDS') //if pipeline build took more than this time, it will be aborted
        disableConcurrentBuilds() // to prevent multiple builds of the same pipeline running at the same time
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
                sh 'echo "This is Build"'
                //sh 'sleep 10' // to test the timeout option, we can increase the sleep time to more than 10 seconds
            }
        }
        stage('Test') {
            steps {
                sh 'echo "This is Test"'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "This is Deploy"'
                //error 'pipeline failed' //to check the post section, failure block
            }
        }
        stage('Print Parameters') {
            steps {
                echo "Hello, ${params.PERSON}!"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle is set to: ${params.TOGGLE}"
                echo "Choice selected: ${params.CHOICE}"
                echo "Password entered: ${params.PASSWORD}"
            }
        }
    }
    post { 
        always { 
            echo "This section will always execute regardless of the build result"
            deleteDir() // to clean the workspace after the build
        }
        success { 
            echo "This section will execute only if the build is successful"
        }
        failure { 
            echo "This section will execute only if the build fails"
        }
    }
}