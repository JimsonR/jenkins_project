pipeline{
    agent{
        label "Jenkins-Agent" // here define a agent
    }
    tools{ // define tools
        jdk 'Java17'
        maven 'Maven3'
    }
}
stages{
    
    stage("Cleanup Workspace"){
        steps{
            cleanWs()
        }
    }

    stage("Checkout From SCM"){
            steps{
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/JimsonR/jenkins_project.git'
            }
        }
        
   