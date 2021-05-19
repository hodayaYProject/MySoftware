pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                script {
                    properties([pipelineTriggers([pollSCM('* * * * *')])])
                }
                git branch: 'main', 'https://github.com/hodayaYProject/MySoftware.git'
            }
        }
        stage('run python') {
            steps {
                script {
                    if (Boolean.valueOf(env.UNIX)) {
                        sh 'python action.py'
                        sh 'python action_screen.py'
                    } else {
                        bat 'python action.py'
                        bat 'python action_screen.py'
                    }
                }
            }
        }
    }
}
