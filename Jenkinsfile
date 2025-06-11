pipeline{
    agent{
        label "Jenkins-Agent-1" // here define a agent
    }
    tools{ // define tools
        jdk 'Java17'
        maven 'Maven3'
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
    stage("Build Application"){
            steps{
                sh "mvn clean package"
            }
        }

    stage("Test application"){
            steps{
                sh "mvn test"
            }
        }
    stage("Sonarqube Analysis"){
            steps{
              script{
                 withSonarQubeEnv(credentialsId: 'jenkins-sonarqube-token'){
                 sh "mvn sonar:sonar"
            }
          }
       
        }
      }
  }
}