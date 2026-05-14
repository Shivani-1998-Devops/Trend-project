pipeline {
    agent {
        node {
            label "maven"
        }
    }

   environment {
    PATH = "/opt/apache-maven-3.9.2/bin:$PATH"
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
                sh 'mvn clean package -DskipTests'
            }
        }

        // stage("test") {
        //     steps {
        //         echo "========testing the application========"
        //     }
        // }

        // stage("deploy") {
        //     steps {
        //         echo "========deploying the application========"
        //     }
        // }

    }

}