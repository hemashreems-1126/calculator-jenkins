
pipeline {
    agent any

    stages {
        stage('SCM Synchronization') {
            steps {
                echo 'Pulling latest code from GitHub...'
                checkout scm
            }
        }

        stage('Static Verification') {
            steps {
                echo 'Checking Maven project...'
                bat '"C:/Apache/apache-maven-3.10.0/bin/mvn.cmd" validate'
            }
        }

        stage('Compilation & Automated Testing') {
            steps {
                echo 'Compiling and testing...'
                bat '"C:/Apache/apache-maven-3.10.0/bin/mvn.cmd" clean package'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }

    post {
        success {
            echo 'CI Pipeline completed successfully!'
        }
        failure {
            echo 'CI Pipeline failed. Check Console Output.'
        }
    }
}
