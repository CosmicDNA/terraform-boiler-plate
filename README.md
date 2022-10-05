# Running Terraform through Docker Compose Tutorial

Starter code for tutorial: [How to use Terraform via Docker Compose for Professional Developers](https://londonappdeveloper.com/2021/04/11/how-to-use-terraform-via-docker-compose-for-professional-developers/).

Also available in [video format](https://youtu.be/nO_Px60YUKg).

This tutorial is an excerpt from our course: [DevOps Deployment Automation with Terraform, AWS and Docker](https://londonapp.dev/devops-aws-terraform).


## Pre-requisites

Before following this tutorial you will need the following:

 1. Access to an AWS IAM user with permissions to access the console.
 2. [aws-vault](https://github.com/99designs/aws-vault) installed and configured with your AWS admin account.
 3. [Docker Desktop](https://www.docker.com/products/docker-desktop) (if using Linux, you'll need to install Docker and Docker Compose separately).

# Applied commands
```bash
# Setup credentials in current terminal session
aws-vault exec --duration=12h account-name

# docker-compose -f deploy/docker-compose.yml run --rm terraform init
make tf-init
# docker-compose -f deploy/docker-compose.yml run --rm terraform fmt
make tf-fmt
# docker-compose -f deploy/docker-compose.yml run --rm terraform validate
make tf-validate
# docker-compose -f deploy/docker-compose.yml run --rm terraform plan -out blueprint
make tf-plan
# docker-compose -f deploy/docker-compose.yml run --rm terraform apply "blueprint"
make tf-apply
# docker-compose -f deploy/docker-compose.yml run --rm terraform destroy
make tf-destroy
```