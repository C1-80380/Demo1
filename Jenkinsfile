pipeline {
    agent any

    stages {
        stage('Build and Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        def imageName = "shrijeet99/mywebite"
                        docker.build(imageName, 'exercise2 .')
                        docker.image(imageName).push()
                    }
                }
            }
        }

        stage('Update Docker Service') {
            steps {
                script {
                    sh 'docker service update --image shrijeet99/mywebsite my-website'
                }
            }
        }
    }
}
