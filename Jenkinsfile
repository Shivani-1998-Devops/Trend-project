pipeline {
    agent {
        node {
            label "maven"
        }
    }

    environment {
        MAVEN_HOME = "/opt/maven"
        PATH = "/opt/maven/bin:${env.PATH}"
    }

    stages {

        stage("debug") {
            steps {
                sh 'hostname -I'
                sh 'hostname'
                sh 'pwd'
            }
        }

        stage("clone-code") {
            steps {
                git branch: 'main',
                url: 'https://github.com/Shivani-1998-Devops/Trend-project.git'
            }
        }

        stage("build") {
            steps {
                sh 'echo $PATH'
                sh 'ls -l /opt/maven/bin'
                sh 'mvn -version'
                sh 'mvn clean package -DskipTests'
            }
        }
    }
}