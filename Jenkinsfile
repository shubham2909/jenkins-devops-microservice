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
    //agent { docker { image 'maven:3.6.3'} }
    //agent { docker { image 'node'} }
    environment {
      mavenHome = tool 'mymaven'
      dockerHome = tool 'myDocker'
      PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
    }
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn --version'
                sh 'docker version'
                echo "Build"
                echo "PATH = $PATH"
                echo "BUILD_NUMBER = $env.BUILD_NUMBER"
                echo "BUILD_ID = $env.BUILD_ID"
                echo "BUILD_URL = $env.BUILD_URL"
                echo "BUILD_ID = $env.BUILD_ID"
                echo "JOB_NAME = $env.JOB_NAME"
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
