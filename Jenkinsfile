pipeline 
{
    agent 
    {
        label 'agent'
    }
def frontendImage="sor4nn/frontend:latest"
def backendImage="sor4nn/backend:latest"
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
