pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time: 10, unit: 'SECONDS') //if pipeline build took more than this time, it will be aborted
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo "This is Build"'
                sh 'sleep 10' // to test the timeout option, we can increase the sleep time to more than 10 seconds
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