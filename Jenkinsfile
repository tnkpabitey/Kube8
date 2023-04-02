pipeline {
    agent any
    parameters {
        string(name: "KeyPairName", defaultValue: "KeyPair", trim: true, description: "Name of an existing EC2 key pair (for SSH-access to the worker node instances)")
        string(name: "WorkerNodesInstanceType", defaultValue: "t2.medium", trim: true, description: "EC2 instance type for the worker nodes")
        string(name: "NumWorkerNodes", defaultValue: "2", trim: true, description: "Number of worker nodes to create")
    }
    stages {
        stage('Deploy Stack') {
            steps {
             sh 'aws --version'
             sh "aws cloudformation create-stack --stack-name EKS-Cluster --template-body file://EKS-Cluster.yml --region 'us-east-1' --capabilities CAPABILITY_NAMED_IAM --parameters ParameterKey=KeyPairName,ParameterValue='${params.KeyPairName}' ParameterKey=WorkerNodesInstanceType,ParameterValue='${params.WorkerNodesInstanceType}' ParameterKey=NumWorkerNodes,ParameterValue='${params.NumWorkerNodes}'"
              }
             }
            }
            }
