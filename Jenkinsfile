pipeline {
    agent any

    environment {
        PATH = "/opt/apache-maven-3.9.2/bin:${env.PATH}"
    }

    stages {

        stage('Git Checkout') {
            steps {
                echo "----------- Git Checkout Started here ----------"

                git branch: 'main',
                url: 'https://github.com/Shivani-1998-Devops/Trend-project.git'

                echo "----------- Git Checkout Completed ----------"
            }
        }

        stage('Build') {
            steps {
                echo "----------- Build Started ----------"

                sh 'mvn -version'
                sh 'mvn clean deploy -Dmaven.test.skip=true'

                echo "----------- Build Completed ----------"
            }
        }
    }
}