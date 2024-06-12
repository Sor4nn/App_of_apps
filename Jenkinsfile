pipeline 
{
    agent 
    {
        label 'agent'
    }
    parameters 
    {
        string(name: 'backendDockerTag', defaultValue: 'latest')
        string(name: 'frontendDockerTag', defaultValue: 'latest')
    }
def frontendImage="sor4nn/frontend:${params.frontendDockerTag}"
def backendImage="sor4nn/backend:${params.frontendDockerTag}"
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
    }
}
