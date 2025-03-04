pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'  // Use the configured Maven installation in Jenkins
    }

    environment {
        POM_PATH = 'pom.xml'  // Update this path if needed
    }

    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'master', 
                    credentialsId: 'github-credentials', 
                    url: 'https://github.com/JosephineBira/JTabbedPaneTask.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    echo "Building the project with Maven..."
                    sh "mvn -f ${POM_PATH} clean install"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo "Running tests..."
                    sh "mvn -f ${POM_PATH} test"
                }
            }
        }

        stage('Package') {
            steps {
                script {
                    echo "Packaging the application..."
                    sh "mvn -f ${POM_PATH} package"
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "Deployment stage - customize this step as needed."
            }
        }
    }

    post {
        always {
            echo 'Build completed!'
        }
        success {
            echo 'Pipeline executed successfully! 🎉'
        }
        failure {
            echo 'Pipeline failed! Check logs. ❌'
        }
    }
}
