pipeline {
    agent any
    stages{
        stage('Build') {
            steps {
                sh '/opt/script-directory/validate.sh'
            }
        }
        stage('Test') {
            steps {
                mail bcc: '', body: "Confirmation de job: ${JOB_URL}", cc: '', from: '', replyTo: '', 
                subject: "Job '${env.JOB_NAME}', Build (${env.BUILD_NUMBER}) attente de confirmation !", to: 'ouftou@gmail.com'
                input 'Voulez-vous autoriser le déploiement ?'
            }
        }
        stage('Deploy') {
            steps {
                sh '/opt/script-directory/deploy.sh'
            }
        }
    }
}
