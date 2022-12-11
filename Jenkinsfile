pipeline{
    tools{
        maven 'mymvn'
    }
    
    agent any
    
    stages{
        stage('ImportRepo'){
            steps{
                echo 'Pipeline Begins Here !!!!'
                git 'https://github.com/KRISSBAJO/spring-boot-docker.git'
            }
        }
        stage('Installation'){
            steps{
                sh 'mvn compile'
            }
        }
        stage('CodeReview'){
            steps{
                sh 'mvn pmd:pmd'
            }
            post{
                success{
                    recordIssues(tools: [pmdParser(pattern: '**/pmd.xml')])
                }
            }
           
        }
        stage(TestCases){
            steps{
               sh 'mvn test'
            }            
        }
        stage('Deploy'){
            steps{
                echo 'Job Ready For Deployment'
                echo 'We are almost done'
                
            }
        }
    }
} 
