@Library('sharedlibrary')_
pipeline
{
    agent any
    stages
    {
        stage('continuousdownload')
        {
            steps
            {
                script
                {
                    cicd.newgit("https://github.com/intelliqittrainings/maven.git")
                }
            }
        }
         stage('continuousbuild')
        {
            steps
            {
                script
                {
                    cicd.newmaven()
                }
            }
        }
         stage('continuousdeployment')
        {
            steps
            {
                script
                {
                    cicd.deploy("172.31.91.156","testapp")
                }
            }
        }
        stage('continuoustesting')
        {
            steps
            {
                script
                {
                    cicd.newgit("https://github.com/intelliqittrainings/FunctionalTesting.git")
                    cicd.runselenium("/home/ubuntu/.jenkins/workspace/pipelinewithlibrary")
                }
            }
        }
        stage('continuousdelivery')
        {
            steps
            {
                script
                {
                    cicd.needapprovals("sirisha")
                    cicd.deploy("172.31.83.73","prodapp")
                }
            }
        }
        
    }
}
