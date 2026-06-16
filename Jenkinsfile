pipeline {
    agent any

    stages {
        stage('cloning the jenkins project') {
            steps {
                git 'https://github.com/vinaybm12/Jenkins-project.git'
            }
        }

        stage('deploy') {
            steps {
                sh '''
                sudo rm -rf /var/www/html/*
                sudo cp -r ./* /var/www/html/
                sudo systemctl reload nginx
                '''
            }
        }
    }

    post {
        success {
            mail(
                bcc: '',
                body: 'Build completed successfully.',
                cc: 'vinu9034@gmail.com',
                from: '',
                replyTo: '',
                subject: 'The build was successfully completed',
                to: 'vinaybm1206@gmail.com'
            )
        }

        failure {
            mail(
                bcc: '',
                body: 'Build failed.',
                cc: 'vinu9034@gmail.com',
                from: '',
                replyTo: '',
                subject: 'The build failed',
                to: 'vinaybm1206@gmail.com'
            )
        }
    }
}
