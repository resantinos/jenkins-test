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
                sh 'scp -o StrictHostKeyChecking=no -i "~/.ssh/jenkins_ssh" -P 22 -r build/* myuser@b23bdde70a5b:/usr/share/nginx/html/'
                sh 'ssh -o StrictHostKeyChecking=no -i "~/.ssh/jenkins_ssh" -p 22 myuser@b23bdde70a5b "sudo service nginx reload"'
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
