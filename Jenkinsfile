pipeline {
    agent any

    environment {
        TARGET_DIR = "/home/admin1/jenkins-files"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-pat',
                    url: 'https://github.com/MatrixAlgo/ace-jenkins-demo.git'
            }
        }

        stage('Copy All Files') {
            steps {
                script {
                    sh '''
                    echo "Copying all files from repo to ${TARGET_DIR}..."
                    mkdir -p ${TARGET_DIR}
                    cp -r ${WORKSPACE}/files/* ${TARGET_DIR}/
                    ls -l ${TARGET_DIR}/
                    '''
                }
            }
        }
    }

    post {
        success {
            echo "Files copied successfully!"
        }
        failure {
            echo "Pipeline failed."
        }
    }
}
