pipeline
   {
       agent any
    stages{
        stage ('Code')
        {
            steps {
                git url : "https://github.com/mastermorejayesh/Node-to-do.git" , branch : "master"
                 echo 'code Stage is complited'
            }
        }

         stage ('build Stage')
        {
            steps {
                 echo 'Build Stage is complited'
            }
        }

       stage("push"){
            steps{
                withCredentials([usernamePassword(credentialsId:"docker-login",passwordVariable:"dockerpassword",usernameVariable:"dockerusername")]){
    sh "docker login -u ${env.dockerusername} -p ${env.dockerpassword}"
    sh "docker tag node-app-test-new:latest ${env.dockerusername}/node-to-do CI-CD:latest"
    sh "docker push ${env.dockerusername}/node-to-do CI-CD:latest"
    echo 'Build Stage is complited'
                
                }
            }
        }

         stage ('Run Stage')
        {
            steps {
                 echo 'Run Stage is complited'
            }
        }

         stage ('Deploy stage')
        {
            steps {
                 sh "docker-compose down && docker-compose up -d"
                 echo '*=*=*=*=*=*=*=*=*Deployment sucessfylly complited*=*=*=*=*=*=*=*=*'
            }
        }
    }
   }s
