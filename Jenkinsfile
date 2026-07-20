pipeline
{
    agent any
    stages
    {
        stage('continous downloadd')
        {
            steps
            {
                git 'https://github.com/marutisureshk-glitch/mymaven.git'
            }
        }
        stage('continuous build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continuous deploy')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '2e68caa9-c15a-4e79-818e-6af0b25c71b1', path: '', url: 'http://172.31.25.135:8080')], contextPath: 'test2', war: '**/*.war'
            }
        }
        stage('continuous test')
        {
            steps
            {
                 git 'https://github.com/marutisureshk-glitch/functiontest.git'
                 sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarativepipeline/testing.jar'
            }
        }
       stage('continuous delivery')
       {
           steps
           {
               deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '2e68caa9-c15a-4e79-818e-6af0b25c71b1', path: '', url: 'http://172.31.22.44:8080')], contextPath: 'prod2', war: '**/*.war'
           }
       }
    }
}
