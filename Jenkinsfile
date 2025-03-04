pipeline {
    agent any

    tools {
        maven 'Maven-3.8.1' // Ensure Maven is installed in Jenkins
    }

    environment {
        GIT_REPO = 'https://github.com/JosephineBira/JTabbedPaneTask.git'
        BRANCH = 'main' // Change this if the default branch is different
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: "${BRANCH}", url: "${GIT_REPO}"
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build Successful! '
        }
        failure {
            echo 'Build Failed! '
        }
    }
}
