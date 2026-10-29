pipeline {

    agent any
 
    stages {

 
        stage('Check Docker') {

            steps {

                sh 'docker --version'

            }

        }
 
        stage('Build frontend Image ') {

            steps {

                sh 'docker build -t studylanex-frontend .'
                sh 'docker rm -f studylanex-frontend || true'
                sh 'docker run -d --name studylanex-frontend -p 5173:4173 studylanex-frontend'

            }

        }
 
        stage('Build backend Image') {

            steps {
                 withCredentials([string(credentialsId: 'mongodb-uri', variable: 'MONGO_URI')]) {
                sh 'docker build -t studylanex-backend ./backend'
                sh 'docker rm -f studylanex-backend || true'
                sh 'docker run -d --name studylanex-backend -p 5000:5000  studylanex-backend'

            }

        }

    }

}
 
}



