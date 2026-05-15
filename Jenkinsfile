pipeline {
    agent any

    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages {

        stage('Git Checkout') {
            steps {
                echo "----------- Git Checkout Started ----------"

                git branch: 'main',
                url: 'https://github.com/Shivani-1998-Devops/Trend-project.git'

                echo "----------- Git Checkout Completed ----------"
            }
        }

        stage('Build') {
            steps {
                echo "----------- Build Started ----------"

                sh 'mvn clean deploy -Dmaven.test.skip=true'

                echo "----------- Build Completed ----------"
            }
        }
    }
}