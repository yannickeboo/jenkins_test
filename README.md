# jenkins_test
rm -rf terraform_buckets
sh label: '',script: 'terraform plan -out=/var/jenkins_home/workspace/test41/test1'
sh label: '',script: 'terraform apply --auto-approve'
  sh 'rm -rf /var/jenkins_home/workspace/test42/terraform-refresh-$BUILDVERSION'
  ll