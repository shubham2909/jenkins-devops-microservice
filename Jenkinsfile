//Scripting

// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Integration Test')
//         {
//  		echo "Test 1"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// }

//Declarative

pipeline {
    #agent { docker { image 'maven:3.6.3'} }
    agent { docker { image 'node'} }
    stages {
        stage('Build') {
            steps {
                sh 'node --version'
                echo "Build"
            }
        }
        stage('Test'){
            steps{
                echo "Test"
            }
        }
        stage('Integration Test'){
            steps{
                echo "Integration Test"
            }
        }
    } 
    
    post {
        always {
            echo "I run awesome.I am fine"
        }
        success {
            echo "I run when everything is success"
        }
        failure {
            echo "I run when anything is fail"
        }
    }

}
