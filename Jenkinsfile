pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                echo "Cloning GitHub repository..."
                git branch: 'main', url: 'https://github.com/Adharsh-jai/my_website.git'
            }
        }

        stage('Check Files') {
            steps {
                echo "Listing project files..."
                bat 'dir'
            }
        }

        stage('Build Website') {
            steps {
                echo "Building website files..."
                bat 'if exist build rmdir /S /Q build'
                bat 'xcopy .\\ my_build /E /I /Y'
            }
        }

        stage('Deploy Website') {
            steps {
                echo "Deploying website to server folder..."
                bat 'xcopy my_build C:\\inetpub\\wwwroot /E /I /Y'
            }
        }
    }

    post {
        success {
            echo "🎉 Deployment Successful!"
        }
        failure {
            echo "❌ Deployment Failed!"
        }
    }
}
