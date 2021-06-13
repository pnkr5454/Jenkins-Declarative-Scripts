pipeline{
    agent any
    tools{
        maven 'maven1'
    }
    stages{
        stage("checkout the code from github"){
            steps{
               git credentialsId: 'githubacc', url: 'https://github.com/pnkr5454/my-app' 
            }
        }
        stage("build the code by using maven"){
            steps{
                sh 'mvn clean package'
            }
        }
        stage("deploy the code to tomcat8"){
            steps{
                sshagent(['tomcat_dev']){
                    //rename the war file
                    sh "mv target/*.war target/myweb.war"
                    //copy war file into tomcat server
                    sh "scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.51.152:/opt/tomcat8/webapps"
                    //start and stop the tomcat8
                    sh "ssh ec2-user@172.31.51.152 /opt/tomcat8/bin/shutdown.sh"
                    sh "ssh ec2-user@172.31.51.152 /opt/tomcat8/bin/startup.sh"
                }
            }
        }
    }
}
