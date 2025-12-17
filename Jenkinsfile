pipeline {
    agent any

    environment {
        TARGET_DIR = "/home/admin1"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-pat',
                    url: 'https://github.com/MatrixAlgo/ace-jenkins-demo.git'
            }
        }

        stage('Copy File') {
            steps {
                script {
                    sh '''
                    echo "Copying demo.txt to ..."
                    sudo cp ${WORKSPACE}/files/demo.txt ${TARGET_DIR}/
                    ls -l ${TARGET_DIR}/demo.txt
                    '''
                }
            }
        }
    }

    post {
        success {
            echo "File copied successfully!"
        }
        failure {
            echo "Pipeline failed."
        }
    }
}
