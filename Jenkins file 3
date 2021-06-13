@Library('pnkr5454_libs') _
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
                tomcatdeploy('tomcat_dev','ec2-user','172.31.51.152')
            }
        }
    }
}
