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
}
stages{
stage('test'){
steps{

sh 'terrafrom init'
sh 'terraform paln'
sh 'terraform apply'
}

}

}

}

}




}
