pipeline {
    agent any
    stages {
        stage('Docker Build') {
            steps {
                imageName="test:${BUILD_NUMBER}"
                containerName="test"

                sh script: "docker system prune -af"
                sh script: "docker build -t $imageName ."
                sh script: "docker stop $containerName || true && docker rm -f $containerName || true"
                sh script: "docker run -p 3000:3000 -d --name $containerName $imageName"
            }
        }
    }
}