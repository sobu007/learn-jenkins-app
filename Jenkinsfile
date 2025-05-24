pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
               sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                    cd build
                    if [ -f "index.html" ]; then
    echo "File exists"
    cd ..
    npm test
else
    echo "File does not exist"
fi
               '''
            }
        }
    }
}
