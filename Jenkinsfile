pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                echo "Cloning GitHub repository..."
                git url: 'https://github.com/Adharsh-jai/my_website.git', branch: 'main'
            }
        }

        stage('Check Files') {
            steps {
                echo "Listing project files..."
                bat "dir"
            }
        }

        stage('Build Website') {
            steps {
                echo "Building website files..."
                bat '''
                    if exist my_build rmdir /S /Q my_build
                    mkdir my_build

                    echo Copying HTML file...
                    copy index.html my_build\\

                    echo Copying CSS files if exist...
                    if exist *.css copy *.css my_build\\

                    echo Copying JS files if exist...
                    if exist *.js copy *.js my_build\\
                '''
            }
        }

        stage('Deploy Website') {
            steps {
                echo "🎉 Deployment successful (simulation only)"
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline completed successfully!"
        }
        failure {
            echo "❌ Deployment Failed!"
        }
    }
}
