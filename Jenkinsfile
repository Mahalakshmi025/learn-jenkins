pipeline {
    agent {
        label 'AGENT-1'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo "This is Build"'
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