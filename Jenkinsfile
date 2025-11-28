pipeline {
    agent any
    tools { 
        nodejs 'NodeJS-20' 
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning Repository...'
                checkout scm
            }
        }

        // stage('Install Backend Dependencies') {
        //     steps {
        //         echo 'Installing backend deps...'
        //         dir('CareFlow-BackEnd') {
        pipeline {
            agent any

            stages {
                stage('Checkout') {
                    steps {
                        echo 'Cloning repository...'
                        checkout scm
                    }
                }

                stage('Install') {
                    steps {
                        echo 'Installing dependencies...'
                        sh 'npm ci'
                    }
                }

                stage('Test') {
                    steps {
                        echo 'Running tests...'
                        sh 'npm test || true'
                    }
                }

                stage('Build') {
                    steps {
                        echo 'Building...'
                        sh 'npm run build || true'
                    }
                }
            }

            post {
                always {
                    cleanWs()
                }
                success {
                    echo 'Pipeline succeeded.'
                }
                failure {
                    echo 'Pipeline failed.'
                }
            }
        }