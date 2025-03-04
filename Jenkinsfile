pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/JosephineBira/JTabbedPaneTask'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean install'
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
        always {
            echo 'Build completed!'
        }
        success {
            echo 'Build successful 🎉'
        }
        failure {
            echo 'Build failed ❌'
        }
    }
}
