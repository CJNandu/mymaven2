pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/CJNandu/mymaven2.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'c3555c92-49ab-4488-b2ec-989877cbc85a', path: '', url: 'http://172.31.38.53:8080')], contextPath: 'testapp1000', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarativepipeline3/testing.jar'
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'c3555c92-49ab-4488-b2ec-989877cbc85a', path: '', url: 'http://172.31.36.252:8080')], contextPath: 'prod2', war: '**/*.war'
            }
        }

    }

}

