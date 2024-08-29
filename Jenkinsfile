pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                docker build -t freedom:v1 .
               '''
            }
        }

        stage('Push')
        {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub_id', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')])
            {
                    sh '''
                docker tag freedom:v1 $USERNAME/freedom:v1

                docker login -u $USERNAME -p $PASSWORD

                docker push $USERNAME/freedom:v1

                docker image rm freedom:v1 $USERNAME/freedom:v1
               '''
            }
            }
        }

        stage('deploy')
        {
            steps {
                sh '''
                  docker pull alijs256/freedom:v1
                  docker run -d --name freePalestine -p 80:80 alijs256/freedom:v1
                '''
            }
        }
    }
}
