pipeline {
    agent { label 'Jenkins-Agent' }
    
    tools {
        jdk 'Java17'
        maven 'Maven3'
    }

    stages {
        stage("Cleanup Workspace") {
            steps {
                cleanWs()
            }
        }

        stage("Checkout from SCM") {
            steps { // Fixed: 'steps' must be lowercase
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/kknocompromise/Registered-App'
            }
        }

        stage("Build Application") { // Fixed: Added missing opening double quote
            steps {
                sh "mvn clean package"
            }
        }

        stage("Test Application") {
            steps {
                sh "mvn test"
            }
        }
    }
}
