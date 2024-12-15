pipeline {
  agent any
  stages {
    stage('Create VPC') {
      steps {
        sh 'gcloud compute networks create test-custom-jenkins-vpc --gcp-practice-space --subnet-mode=custom'
      }
    }
    stage('Create Subnets') {
      steps {
        sh 'sleep 40'
        sh 'gcloud compute networks subnets create test-cmd-subnets --gcp-practice-space --range=10.0.0.0/24 --network=test-custom-jenkins-vpc --region=us-central1'
      }
    }
    stage('Create Instance with VPC') {
      steps {
        sh 'gcloud compute instances create instance-jenkins-vpc-subnet --gcp-practice-space --zone=us-central1-f --machine-type=e2-medium --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=test-cmd-subnets --service-account=jenkins@my-project-279-436907.iam.gserviceaccount.com'
      }
    }
  }
}
