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
    environment {
        PIP_BREAK_SYSTEM_PACKAGES = '1'
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

        stage('Deploy application') 
        {
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

       // stage('PytonTest ') {
           // steps {
          //      script {
                    //sh "pip3 install -r test/selenium/requirements.txt"
                    //sh "python3 -m pytest test/frontendTest.py"
         //       }
        //    }
       // }
        
    }



    post {
        always {
                sh "docker-compose down"
                cleanWs()
        }
    }
}
