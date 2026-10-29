pipeline {

    agent any
 
    stages {

 
        stage('Check Docker') {

            steps {

                sh 'docker --version'

            }

        }
 
        stage('Build frontend Image') {

            steps {

                sh 'docker build -t studylanex-frontend .'
                sh 'docker run -p 8080:80 studylanex-frontend'

            }

        }
 
        stage('Build backend Image') {

            steps {

                sh 'docker build -t studylanex-backend ./backend'
                sh 'docker run -p 5000:5000  studylanex-backend'

            }

        }

    }

}
 