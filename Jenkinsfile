pipeline {
    agent { label 'dev'}
    tools {
        maven 'maven'
    }

    stages {
        stage('SCM') {
            steps {
               git branch: 'main', url: 'https://github.com/Banda-Sirichandana/srinivas.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
                sh 'mvn -v'
            }
        }
        stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://13.233.102.113:8081/')], contextPath: 'app', war: '**/*.war'
                
            }
        }
    }
}
