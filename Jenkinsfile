pipeline {
    agent any
    
    environment {
        registry = "asvinwin123/node-sample"
        registryCredential = "b00de5ae-26b1-4813-8145-0118a47e7e78"
    }

    stages {
        stage('Build & Push Image') {
            steps {
                script {
                    def appimage = docker.build registry + ":$BUILD_NUMBER"
                    docker.withRegistry( '', registryCredential ) {
                        appimage.push()
                        appimage.push('latest')
                    }
                }
                echo 'image build & push success'
            }
        }
    }
}
