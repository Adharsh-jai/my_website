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

                // Create clean build folder
                bat 'if exist my_build rmdir /S /Q my_build'
                bat 'mkdir my_build'

                // Copy only website files
                bat 'copy index.html my_build\\'
                bat 'copy *.css my_build\\ 2>nul'
                bat 'copy *.js my_build\\ 2>nul'
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
