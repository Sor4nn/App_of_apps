pipeline 
{
    agent 
    {
        label 'agent'
    }
def frontendImage="sor4nn/frontend:${params.frontendDockerTag}"
def backendImage="sor4nn/backend:${params.frontendDockerTag}"
    parameters 
    {
        string(name: 'backendDockerTag', defaultValue: 'latest')
        string(name: 'frontendDockerTag', defaultValue: 'latest')
    }

currentBuild.description = "Backend Version: ${params.backendDockerTag}, Frontend Version: ${params.frontendDockerTag}"
    stages 
    {
        stage('Get Code') 
        {
            steps 
            {
                checkout scm
            }
        }
        stage('Build Output') 
        {
            steps 
            {
                sh "echo currentBuild.description"
            }
        }
    }
}
