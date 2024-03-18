pipeline{
    agent{
        label 'master"
    }
    stages{
        stage("Fetch latest code "){
            steps{
                echo "========executing A========"
                git credentialsId: 'github', url: 'https://gitbub.com/monsad/qa'
            }
          }
        stage('TF Init&Plan') {
            steps {
              sh 'terraform init'
              sh 'terraform plan'
            }
          }
        stage('Approval')
            steps {
              script {
                def userInput = input(id: 'confirm', message: 'Apply Terraform?', parameteres: [ [$class: 'BooleenParameterDefinition', defaultValue: false, description: 'Apply terraform', name; 'confirm'] ])
              }
            }
        }
        stage('TF Apply') {
          steps {
            sh 'terraform apply -input=false'
        }
      }
  }
