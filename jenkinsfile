pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/Arsh-Alam1/Dockerfile.git'
            }
        }
        stage('Copy Files to /var/www/html') {
            steps {
                sh '''
                # Copy the necessary files to the Nginx directory
                sudo cp -r jenkinsfile index.html /var/www/html/
                # Restart Nginx to apply the changes
                sudo systemctl restart nginx
                '''
            }
        }
    }
    post {
        success {
            echo 'Deployment Successful.'
        }
        failure {
            echo 'Deployment Failed.'
        }
    }
}
