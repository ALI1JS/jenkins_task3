pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
               sh 'docker build -t freedom:v1 .'
            }
        }

        stage ('Push')
        {
            steps {
            withCredentials([usernamePassword(credentialsId: 'dockerhub_id', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')])
            {
               sh ''' 
                docker login -u $USERNAME -p $PASSWORD
                docker tag freedom:v1 $USERNAME/freedom:v1
                docker push $USERNAME/freedom:v1
               '''
            }
            sh 'docker image rm freedom:v1'
         }
        }
    }
}