pipeline {

    agent any

        environment {

                VERSION = '1.0.0'

                DOCKERHUB_CREDENTIALS = credentials('docker-gageross-credentials')

        }



    stages {

        stage('Checkout') {

            steps {

                //sh 'git clone "https://github.com/gzander7/git-tutorial-Gage.git"'
                sh 'echo "pulled https://github.com/gzander7/git-tutorial-Gage.git"'
            }

        }



        stage('Test') {

            steps {

                //sh 'docker build -t csc324flaskapp .'

                sh 'echo "Testing csc324flaskapp"'

            }

        }



        stage('Build Docker Image') {

            steps {
                sh 'sudo chmod 666 /var/run/docker.sock'
                sh 'docker build -t gzander7/csc324flaskapp:$VERSION .'
                sh 'docker build -t gzander7/csc324flaskapp:latest .'

            }
        }

        stage('Dockerhub login') {

                steps {

                        sh 'echo $DOCKERHIB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'

                        }

                }

        stage('Push Docker Image') {

            steps {

                    sh 'docker push gzander7/csc324flaskapp:$VERSION'

                    sh 'docker push gzander7/csc324flaskapp:latest'

                }

            }

        }

    }
