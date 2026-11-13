
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
bat '"C:/Users/HEMASHREE M S/Downloads/maven-mvnd-1.0.6-windows-amd64/maven-mvnd-1.0.6-windows-amd64/bin/mvnd.cmd" validate'            }
        }

        stage('Compilation & Automated Testing') {
            steps {
                echo 'Compiling and testing...'
bat '"C:/Users/HEMASHREE M S/Downloads/maven-mvnd-1.0.6-windows-amd64/maven-mvnd-1.0.6-windows-amd64/bin/mvnd.cmd" clean package'            }
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
