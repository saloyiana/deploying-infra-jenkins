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

sh "terraform init -backend-config="bucket=remote-state-${TF_NAMESPACE}" -backend-config="key=${TF_NAMESPACE}/labs/terraform.tfstate" -backend-config="dynamodb_table=locks-${TF_NAMESPACE}""

} 
}
stage('plan'){
steps{
sh 'terraform paln'
}
}
stage('apply'){
steps{
sh 'terraform apply'
}
}
}
}
