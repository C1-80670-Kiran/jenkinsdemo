pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git 'https://github.com/C1-80670-Kiran/jenkinsdemo.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_T27Taos6Hn5T7R_Nvs0UkQ9lUDQ | /usr/bin/docker login -u kirandada0303723 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker build -t kirandada0303723/mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
               sh '/usr/bin/docker image push kirandada0303723/mywebsite'
            }
        }
        stage ('docker remove service') {
            steps {
               sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
               sh '/usr/bin/docker service create --name myservice -p 9090:80 --replicas 5 kirandada0303723/mywebsite'
            }
        }
    }
}

