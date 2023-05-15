pipeline {
    environment {
        registry = 'sound-em'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Build Docker Image') {
            agent any
            steps {
                imageName=test:${BUILD_NUMBER}
                containerName=test

                docker system prune -af
                docker build -t $imageName .
                docker stop $containerName || true && docker rm -f $containerName || true
                docker run -p 3000:3000 -d --name $containerName $imageName
            }
        }

    }
}