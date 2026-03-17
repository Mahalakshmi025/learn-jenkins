pipeline {
    agent any
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
            }
        }
    }
    post { 
        always { 
            echo "This section will always execute regardless of the build result"
        }
        success { 
            echo "This section will execute only if the build is successful"
        }
        failure { 
            echo "This section will execute only if the build fails"
        }
    }
}