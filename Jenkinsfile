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
        
        stage('Set Variables') 
        {
            steps 
            {
                script 
                {
                    def frontendImage = "sor4nn/frontend:${params.frontendDockerTag}"
                    def backendImage = "sor4nn/backend:${params.backendDockerTag}"
                    currentBuild.description = "Backend Version: ${params.backendDockerTag}, Frontend Version: ${params.frontendDockerTag}"
                }
            }
        }
    }
}
