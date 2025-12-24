pipeline {
    agent { label 'Jenkins-Agent' }
    
    tools {
        jdk 'Java17'
        maven 'Maven3'
    }

    stages {
        stage("Checkout from SCM") {
            steps {
                // Using the exact URL from your successful log
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/kknocompromsie/Registered-App'
            }
        }

        stage("Build Application") {
            steps {
                sh "ls -ltr" 
                sh "mvn clean package"
            }
        }

        stage("Test Application") {
            steps {
                sh "mvn test"
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
