# Add Permissions Jenkins
- Following
```
sudo chown -R jenkins:jenkins /var/www/project_name
```

- Restart Jenkins
```
sudo systemctl restart jenkins
```

# Script Jenkins Laravel
pipeline {
    agent any

    environment {
        // Define environment variables if needed
        DEPLOY_DIR = '/var/www/project_name'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/username/repo_name.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install composer dependencies
                sh 'composer install --no-interaction --prefer-dist --optimize-autoloader'
            }
        }

        stage('Deploy') {
            steps {
                sh "cp -R * ${DEPLOY_DIR}/"
                sh "cd ${DEPLOY_DIR} && composer install --no-interaction --prefer-dist --optimize-autoloader"
            }
        }

        stage('Clear Cache') {
            steps {
                sh "php artisan optimize"
                sh "php artisan optimize:clear"
            }
        }

        stage('Migrate Database') {
            steps {
                sh "cd ${DEPLOY_DIR} && php artisan migrate --force"
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
