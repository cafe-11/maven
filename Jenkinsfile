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
                git 'https://github.com/intelliqittrainings/maven.git'
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
