pipeline
{
    agent any
    tools 
    {
        maven 'Maven_New'
    }
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git branch: 'main', credentialsId: 'git_creds', url: 'https://github.com/cafe-11/maven.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn clean package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: 'tomcat_creds', path: '', url: 'http://172.31.82.18:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
       
    }
    
    post
    {
         always 
         {
            archiveArtifacts artifacts: '**/*.war', fingerprint: true
         }
       
    }
    
    
    
    
    
    
}
