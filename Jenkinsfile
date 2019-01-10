pipeline{
    agent any
    parameters {
      string(defaultValue: "plan",  name: "action",  description: "Do you want plan/apply/destroy ")
    }
    stages{
        stage("Pull repo"){
            steps{
                git 'https://github.com/kolomyya/terraform.git'
            }
        }
        stage("Terraform init"){
            steps{
                ws("${workspace}/dev/kubernetes_cluster"){
                    sh "terraform init"
                }
            }
        }
        stage("Terraform Apply"){
            steps{
                ws("${workspace}/dev/kubernetes_cluster"){
                    sh "terraform ${action} -auto-approve"
                }
            }
        }
    }
}
