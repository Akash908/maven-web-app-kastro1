pipeline{
    agent any

    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deplot to tomcat server'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat-creds', path: '', url: 'http://13.234.35.217:9090/')], contextPath: null, war: '**/*war'
            }
        }
    }

}