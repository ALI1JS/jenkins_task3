/* groovylint-disable-next-line CompileStatic */
pipeline{
    agent  any

    stages {
        stage('Build Stage')
        {
            sh 'docker build -t freedom_image:v1 .'
        }
    }
}
