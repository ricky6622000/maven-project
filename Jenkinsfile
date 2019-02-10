pipeline 
{
        agent any 
        tools
        {
            jdk "java8"
            maven "maven"
        }
        stages
        {
            stage('initializing')
            {
                steps
                {
                    echo("This is initializing")
                }
            }
            stage('Build')
            {
                steps
                {
                    echo("This is Build")
                    sh label: '', script: 'mvn clean package checkstyle:checkstyle'
                }
                post
                {
                    success
                    {
                        echo("See checkstyle analysis result")
                        checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
                        archive '**/*.war'
                        junit '**/surefire-reports/*.xml'
                    }
                }
            }
            stage('Deploy')
            {
                steps
                {
                    echo("This is Deployment")
                }
            }
        }
}