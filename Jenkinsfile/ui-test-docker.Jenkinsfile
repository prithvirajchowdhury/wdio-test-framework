pipeline {
    agent {
        docker {
            image 'build-node:latest'
            args '-p 5920:5920 -u root:root'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                // Get code from a GitHub repository
                git branch: 'main', credentialsId: '2b2cdf6e-db62-49e3-847c-0b57aa683b75', url: 'https://github.com/prithvirajchowdhury/wdio-test-framework.git'
            }
        }
        stage('Build') {
            steps {
                sh 'export DISPLAY=:20'
                sh 'Xvfb :20 -screen 0 1366x768x16 &'
                sh 'x11vnc -passwd TestVNC -display :20 -N -forever &'
                sh 'npm install'
                }
            }
          stage('Test') {
              steps {
                sh 'npx wdio run ./wdio.conf.js'
              }   
            } 
            post {      
                always {          
                    junit '*.xml'
                }
            }
    }
}

