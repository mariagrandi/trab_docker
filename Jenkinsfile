pipeline {
    agent any
    stages{
        stage ("reiniciando o docker"){
            steps {
               sh """
                docker rm -f nginx_cont
                docker image rm nginx_image
                docker build -t nginx_image .
                docker run --name nginx_cont -p 8081:80 -d nginx_image
                """ 
            }
        }
    }
}