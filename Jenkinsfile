pipeline {
    agent any

    stages {
        stage('Install Apache2') {
            steps {
                sh 'sudo apt-get update -y'
                sh 'sudo apt-get install apache2 -y'
                sh 'sudo systemctl start apache2'
                sh 'sudo systemctl enable apache2'
            }
        }

        stage('Check Apache2 version') {
            steps {
                sh 'apache2 -v'
            }
        }

        stage('Errors check') {
            steps {
                sh """
                    sudo grep -E '\" [45][0-9][0-9] ' /var/log/apache2/access.log | awk '{print \$9 " -> " \$7}'
                """
            }
        }

    }
}