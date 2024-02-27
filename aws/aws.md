docker build -t project-tag .
docker tag project-tag:latest xxx.dkr.ecr.eu-central-1.amazonaws.com/project-tag:latest 
aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin xxx.dkr.ecr.eu-central-1.amazonaws.com 
docker push xxx.dkr.ecr.eu-central-1.amazonaws.com/project-tag:latest 
login to aws and find apprunner than press deploy (until we have a pipeline)