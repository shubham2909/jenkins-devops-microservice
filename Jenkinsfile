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
    agent any
    stages {
        stage('Build') {
            steps {
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
    } post {
        always {
            echo "I run awesome.I am fine"
        }
        success {
            echo "I run when everything is success"
        }
        faiure {
            echo "I run when anything is fail"
        }
    }

}
