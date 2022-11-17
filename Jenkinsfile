pipeline{
    agent any
    
    stages{
        stage("clean up"){
            steps{
                deleteDir()
            }
        }
        stage("git clone"){
            steps{
                git credentialsId: 'git_passwords', url: 'https://github.com/shrutideodikar/cg_jenkins.git'
            }
        }
        stage("build"){
            steps{
               bat 'mvn clean install'
            }
        }
        stage("Test"){
            steps{
                bat 'mvn test'
            }
        }
        stage("copy war to tomcat"){
            steps{
                bat 'copy target\\CCdemo.war D:\\Demo\\apache-tomcat-9.0.69\\webapps'
            }
        }
        stage("tomcat folder"){
            steps{
                sleep(5)
                bat 'D:\\Demo\\apache-tomcat-9.0.69\\bin\\startup.bat'
                sleep(300)
            }
        }
      
        stage("Completed sucessfuly!!"){
            steps{
                echo "completed!!"
            }
        }

    }
}