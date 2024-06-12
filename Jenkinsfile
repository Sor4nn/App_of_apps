def frontendImage = "sor4nn/frontend:${params.frontendDockerTag}"
def backendImage = "sor4nn/backend:${params.backendDockerTag}"

pipeline 
{
    agent 
    {
        label 'agent'
    }
    
    parameters 
    {
        string(name: 'backendDockerTag', defaultValue: 'latest', description: '')
        string(name: 'frontendDockerTag', defaultValue: 'latest', description: '')
    }
    
    stages 
    {
        stage('Get Code') 
        {
            steps 
            {
                checkout scm
            }
        }
        
        stage('Version Info') 
        {
            steps 
            {
                script 
                {
                    currentBuild.description = "Backend Version: ${params.backendDockerTag}, Frontend Version: ${params.frontendDockerTag}"
                }
            }
        }
    }
}
