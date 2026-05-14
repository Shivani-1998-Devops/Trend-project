pipeline{
    agent{
        node{
            label "maven"
        }
    }
    stages{
        stage("clone-code"){
            steps{
                git branch: 'main', url: 'https://github.com/Shivani-1998-Devops/Trend-project.git'
            }
        }
    //     stage("test"){
    //         steps{
    //             echo "========testing the application========"
    //         }
    //     }
    //     stage("deploy"){
    //         steps{
    //             echo "========deploying the application========"
    //         }
    //     }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}