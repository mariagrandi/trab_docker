pipeline {
    agent any
    stages{
        stage ("reiniciando o docker"){
            steps {
               sh """
                docker rm -f nginx_cont
                docker image rm nginx_image
                """ 
            }
        }
        stage ("construindo nova imagem"){
            steps {
               sh """
                docker build -t nginx_image .
                """ 
            }
        }
        stage ("construindo novo container"){
            steps {
               sh """
                docker run --name nginx_cont -p 8081:80 -d nginx_image
                """ 
            }
        }
    }
    post {
        always {
            emailext (
                to: 'mvrg1603@gmail.com',
                body: '${DEFAULT_CONTENT}',
                mimeType: 'text/html',
                subject: '${DEFAULT_SUBJECT}',
                replyTo: 'mvrg1603@gmail.com'
            )
        }
    }
}