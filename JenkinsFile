pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/username/simple-php-ci.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'composer install'
            }
        }
        stage('Run Unit Tests') {
            steps {
                sh './vendor/bin/phpunit'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t simple-php-app .'
            }
        }
        stage('Deploy (Run Container)') {
            steps {
                sh 'docker run -d -p 8000:8000 --name php_app simple-php-app'
            }
        }
    }
}
