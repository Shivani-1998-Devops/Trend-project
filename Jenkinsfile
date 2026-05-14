pipeline {
    agent {
        node {
            label "maven"
        }
    }

 environment {
    MAVEN_HOME = "/opt/maven"
    PATH = "${MAVEN_HOME}/bin:${env.PATH}"
}
    stages {

        stage("clone-code") {
            steps {
                git branch: 'main',
                url: 'https://github.com/Shivani-1998-Devops/Trend-project.git'
            }
        }

        stage("build") {
            steps {
                sh 'mvn -version'
                sh 'mvn clean package -DskipTests'
            }
        }
    }
}