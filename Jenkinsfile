pipeline {
agent {
docker {
image 'bryandollery/terraform-packer-aws-alpine'
args '-u root --entrypoint='
}
}
environment {
CREDS = credentials('sara-aws')
AWS_ACCESS_KEY_ID="${CREDS_USR}"
AWS_SECRET_ACCESS_KEY="${CREDS_PSW}"
OWNER="sarah"
AWS_PROFILE="kh-labs" 
PROJECT_NAME="sarah-webserver"
TF_NAMESPACE="sarah"
}
stages{
stage('build'){
steps{

sh ' terraform init -backend-config="bucket=devops-bootcamp-remote-state-sarah" -backend-config="key=sarah/labs/terraform.tfstate" -backend-config="dynamodb_table=devops-bootcamp-locks-sarah"'
} 
}
stage('plan'){
steps{
sh 'terraform plan'
}
}
stage('apply'){
steps{
sh 'terraform apply'
}
}
}
}
