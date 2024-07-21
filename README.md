I am Done this on aws ubuntu ec2 ;
commands for install aws cli in ubuntu:
sudo apt update
sudo apt install -y unzip curl
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install

Note: install docker in your machine

steps :
Steps
1. Create an ECR Repository
i. Navigate to the Amazon ECR console.
ii. Click on Create repository.
iii. Enter ‘Pratik’ as the repository name.
2. Create an IAM Policy
i. Navigate to the IAM console.
ii. Select policies from the sidebar.
iii. Click on Create policy.
Add the following JSON content to the
policy document.
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ecr:GetAuthorizationToken",
        "ecr:BatchCheckLayerAvailability",
        "ecr:GetDownloadUrlForLayer",
        "ecr:GetRepositoryPolicy",
        "ecr:DescribeRepositories",
        "ecr:ListImages",
        "ecr:DescribeImages",
        "ecr:BatchGetImage",
        "ecr:GetLifecyclePolicy",
        "ecr:GetLifecyclePolicyPreview",
        "ecr:ListTagsForResource",
        "ecr:PutImage",
        "ecr:UploadLayerPart",
        "ecr:InitiateLayerUpload",
        "ecr:DescribeImageScanFindings",
        "ecr:CompleteLayerUpload"
      ],
      "Resource": "*"
    }
  ]
}
v. Give name for the policy.
vi. Click on Create policy.
3. Create an IAM User and Attach Policy
i. Navigate to the IAM console.
ii. Select Users from the sidebar.
iii. Click on Add user.
iv. Enter a username.
v. Click on Next: Permissions.
vi. Select Attach Policy directly
vii. Search and select the policy that we created
earlier.
viii. Click on Next: Review.
ix. Click on Create user.
x. Click on the created user and go to the
Security credentials tab.
xi. Click on Create access key.
xii. Save the access key and secret key for later
use.
4. Configure AWS CLI
i. Open a terminal (I’m using killercoda
environment).
ii. Run the aws configure command:
iii. Enter the access key and secret key when
prompted.
5. Create a Dockerfile and index.html file
i. Create a
‘Dockerfile’ with the following
content:
ii. Create an
‘index.html’ file with a simple
message.
6. Build and Push Docker Image to ECR
7. Create an ECS Cluster
i. Navigate to the Amazon ECS console.
ii. Click on Clusters in the sidebar.
iii. Click on Create Cluster.
iv. Enter a name for the cluster
v. Click on Create.
8. Create a Task Definition
i. Navigate to the Amazon ECS console.
ii. Click on Task Definition in the sidebar.
iii. Click on Create new Task Definition.
iv. Enter a name for task definition.
v. In the Container section, click on Add
container.
vi. Enter a name for the container.
vii. In the Image field, enter the URI of the
ECR repository.
viii. Click on Create.
9. Create a Service
i. Navigate to ECS console.
ii. Click on Clusters in the sidebar.
iii. Select the cluster created earlier.
iv. Click on Create under Services tab.
v. Under Environment, select Capacity
provider strategy and choose FARGATE.
vi. Under Deployment configuration, select
Task.
vii. Task definition: Select the created task
definition.
viii. Click Next and Create service.
10. Access the Deployed Application
i. Navigate to the Amazon ECS console.
ii. Select the cluster and click on the service
created earlier.
iii. Click on Task tab and select the running
task.
iv. Under Configuration, click on Open address by public ip enter on web browser.
v. Open the address in a web browser to and
navigate to the public IP address to view the
‘index.html’ page created earlier.
By following these steps you’ve successfully
deployed an application on AWS ECS using ECR
and Docker.
