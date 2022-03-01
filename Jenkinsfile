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
        //stage('Test'){
            //steps{
                //echo "Test"
            //}
        //}
        stage('Compile'){
            steps{
                sh "mvn clean compile"
            }
        }
        
        stage('Test'){
            steps{
                sh "mvn test"
            }
        }
        
        stage('Integration Test'){
            steps{
                sh "mvn failsafe:integration-test failsafe:verify"
            }
        }
        
        stage('Package'){
            steps{
                sh "mvn package -DskipTests"
            }
        }
        
        stage('Build docker Image'){
            steps {
                //docker build -t shubham291110/currency-exchange-jenkins-push:${env.BUILD.TAG}
                script{
                    dockerImage = docker.build("shubham291110/currency-exchange-jenkins-push:{$env.BUILD_TAG}")
                }
           }
    } 
        
         
        stage('Push the Docker Image'){
            steps {
                script{
                    docker.withRegistry('','dockerhub'){
                        dockerImage.push();
                        dockerImage.push('latest');
                    }
                }
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
