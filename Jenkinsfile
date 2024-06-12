def frontendImage = "sor4nn/frontend"
def backendImage = "sor4nn/backend"

pipeline {
    agent {
        label 'agent'
    }

    parameters {
        string(name: 'backendDockerTag', defaultValue: 'latest', description: '')
        string(name: 'frontendDockerTag', defaultValue: 'latest', description: '')
    }

    stages {
        stage('Get Code') {
            steps {
                checkout scm
            }
        }
        
        stage('Version Info') {
            steps {
                script {
                    currentBuild.description = "Backend Version: ${params.backendDockerTag}, Frontend Version: ${params.frontendDockerTag}"
                }
            }
        }
        
        stage('Remove Images') {
            steps {
                script {
                    sh "docker rm -f frontend || true"
                    sh "docker rm -f backend || true"
                    echo "Removed Frontend & Backend Containers"
                }
            }
        }

        stage('Deploy application') {
            steps {
                script {
                    withEnv([
                        "FRONTEND_IMAGE=${frontendImage}:${params.frontendDockerTag}", 
                        "BACKEND_IMAGE=${backendImage}:${params.backendDockerTag}"
                    ]) {
                        sh "docker-compose up -d"
                    }
                }
            }
        }
    }

    post {
        always {
            steps {
                sh "docker-compose down"
                cleanWs()
            }
        }
    }
}
