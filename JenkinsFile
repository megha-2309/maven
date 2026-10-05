pipeline{
    agent any
        stages{
            stage('ContinuousDownload'){
                steps{
                   git 'https://github.com/IntelliqDevops/maven.git'
                }
            }
            stage('ContinuosBuild'){
                steps{
                sh 'mvn package'
                }
            }
            stage('ContinuousDeployment'){
                steps{
                  sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@172.31.2.222:/var/lib/tomcat10/webapps/testapp.war'
                }
            }
            stage('ContinuousTesting'){
                steps{
                  git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                  sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
                }
            }
            stage('ContinuousDelivery'){
                steps{
                    sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@172.31.9.15:/var/lib/tomcat10/webapps/prodapp.war'
                }
                
            }
        }
    
}
