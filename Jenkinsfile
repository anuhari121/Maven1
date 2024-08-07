pipeline
{
    agent any
    stages
    {
        stage('Continous download')
        {
            steps
            {
                git 'https://github.com/anuhari121/Maven1.git'
            }
        }
        stage('continous build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continous deploy')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'f2a3e2c3-6e19-4063-96ca-39db4fac4c59', path: '', url: 'http://172.31.29.8:8080')], contextPath: 'hari', war: '**/*.war'
            }
        }
        stage('continous testing')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java  -jar /var/lib/jenkins/workspace/Ramesh/testing.jar'
            }
        }
        stage('continous delevery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'f2a3e2c3-6e19-4063-96ca-39db4fac4c59', path: '', url: 'http://172.31.23.157:8080')], contextPath: 'ammu', war: '**/*.war'
            }
        }
    }
}
