pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the website...'
                // You can copy your HTML, CSS, and other necessary files to a build directory here
                sh 'mkdir -p build'
                sh 'cp index.html styles.css build/'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add any test commands if needed
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the website...'
                // You can deploy the content to a server or hosting service here
                // For simplicity, we'll just print a message
                sh 'echo "Deploying the website!"'
                sh 'scp -i "~/.ssh/jenkins_ssh" -P 22 -r build/* myuser@4bd3b28ac32a:/usr/share/nginx/html/'
                ssh -i "~/.ssh/jenkins_ssh" -p 22 myuser@4bd3b28ac32a "service nginx reload"
                ssh -i "~/.ssh/jenkins_ssh" -p 22 myuser@4bd3b28ac32a "service nginx restart"
    }
}

            }
        }
    

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
    }
