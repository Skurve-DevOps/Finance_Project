pipeline{
    agent any
    stages{
        stage('Stage1: checkout the code from github'){
            steps{
                 git url: 'https://github.com/Skurve-DevOps/Finance_Project/'
                 echo 'github url checkout'
            }
        }
        stage('Stage2: codecompile'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('Stage3: codetesting'){
            steps{
                sh 'mvn test'
            }
        }
        stage('Stage4: QA'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('Stage5: package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('Stage6: run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('Stage7: port expose'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }   
    }
}
