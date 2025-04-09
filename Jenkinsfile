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
         stage('test') {
            agent {
                docker {
                    image 'node:20-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                   echo "lancement des tests"
                   test -f dist/index.html
                   npm run test
                '''
            }
        }
    }
}
