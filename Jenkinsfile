pipeline{
    agent any
    tools{
            maven 'maven'
            
        }
    stages{
        stage("build"){
            steps{
                script{
                    echo "building"
                    sh 'mvn package'

                }

            }
        }
        stage("build image"){
            steps{
                script{
                    echo"imaging"
                    withCredentials([usernamePassword(credentialsId: 'server',passwordVariable:'pass',usernameVariable:'user')]){
                    sh 'docker build -t  tushar24sharma/docker:2.1 . '
                    sh "echo $pass | docker login -u $user --password-stdin"
                    sh 'docker push tushar24sharma/docker:2.1 '
                    }
                   
                }
            }
        }
        stage("deploy"){
            steps{
                script{
                        echo "deployed"

                }

            }
        }
    }
}
