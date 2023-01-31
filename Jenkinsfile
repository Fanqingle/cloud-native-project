pipeline {
    agent none

    stages {
        stage('Clone Code') {
            agent {
                label 'master'
            }
            steps {
                echo "1. Git Clone Code Stage"
                git url: "https://git.nju.edu.cn/tumi233/test.git"
            }
        }

        stage('Maven Build') {
            agent {
                docker {
                    image 'maven:latest'
                    args '-v /root/.m2:/root/.m2'
                }
            }
            steps {
                echo "2.Maven Build Stage"
                sh 'mvn -B clean package -Dmaven.test.skip=true'
            }
        }
    }
}