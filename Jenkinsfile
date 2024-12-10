pipeline
{
    agent any
    environment
    {
        NODE_VERSION = '20.x'
    }
    tools
    {
        notejs "${NODE_VERSION}"
    }
    stages
    {
        stage('Checkout')
        {
            steps
            {
                git branch: 'main', url: 'https://github.com/JanaDN/StudentRegestryAppDemo' 
            }
        }

        stage("Install dependencies")
        {
            steps
            {
                script
                {
                    bat 'npm install'
                }
            }
        }

        stage("Start application and run tests")
        {
            steps
            {
                script
                {
                    bat 'npm install &'
                    bat 'wait-on http://localhost:8090'
                    bat 'npm test'
                }
            }
        }
    }
    post
    {
        always
        {
            echo "CI pipeline completed"
        }
    }
}