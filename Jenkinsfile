pipeline {
    agent any

    stages {
        stage('build') {
            agent {
                docker {
                    image 'node:20-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo 'jenkins va installer les dépendances'
                    ls -al
                    npm ci
                    echo 'jenkins va lancer le build'
                    npm run build
                    echo 'fin'
                    ls -al
                '''
            }
        }
    }
}
