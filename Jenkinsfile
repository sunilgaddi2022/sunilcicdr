pipeline {
    agent any

    environment {
        SSH_USER = 'ubuntu'
        SERVER_IP = '35.170.56.91'
    }

    stages {
        stage('Build') {
            steps {
                
                withCredentials([file(credentialsId: '2b883b53-9008-4898-92f3-3bd33ba42911', variable: 'SSH_KEY')]) {
                    sh '''
                        echo "Starting Deployment..."

                        SSH_KEY_FILE=temp_ssh_key
                        cp $SSH_KEY $SSH_KEY_FILE
                        chmod 600 $SSH_KEY_FILE

                        SSH_OPTIONS="-o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null"

                        ssh $SSH_OPTIONS -i $SSH_KEY_FILE ${SSH_USER}@${SERVER_IP} 'whoami'
                        
                        rm -f $SSH_KEY_FILE
                    '''
                }
            }
        }
        stage('Test') {
            steps {
                sh 'pytest'
            }
        }
        stage('Deploy') {
            steps {
                sh 'fab deploy'
            }
        }
    }

    post {
        success {
            mail to: 'sunilgaddi424@gmail.com',
            subject: 'Pipeline Success',
            body: 'Your pipeline has succeeded.'
        }
        failure {
            mail to: 'sunilgaddi424@gmail.com',
            subject: 'Pipeline Failure',
            body: 'Your pipeline has failed.'
        }
    }
}
