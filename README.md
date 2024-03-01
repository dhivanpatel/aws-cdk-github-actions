## GitHub Actions Deployment with AWS CDK

This repository provides a template for using GitHub Actions to deploy resources to AWS using the AWS Cloud Development Kit (CDK). It utilizes OpenID Connect (OIDC) authentication to securely access your AWS account from GitHub Actions workflows.

### Overview

GitHub Actions allows you to automate your software development workflows directly from your GitHub repository. With this template, you can set up continuous deployment (CD) pipelines to automatically deploy your infrastructure to AWS whenever changes are pushed to your repository.

### Pre-requisites

1. **AWS Account**: You need an AWS account to deploy resources using CDK.
2. **GitHub Repository**: Create a GitHub repository to host your code and workflows.
3. **AWS CDK Installed**: Install the AWS CDK CLI on your local machine to interact with CDK projects.
4. **AWS IAM Role**: Set up an IAM role in your AWS account with appropriate permissions for GitHub Actions.

### Setup Steps

#### 1. Configuring AWS IAM Role

- Create an IAM role in your AWS account that allows GitHub Actions to deploy resources using CDK.
- Attach the necessary policies to the IAM role, such as `AmazonS3FullAccess`, `AmazonDynamoDBFullAccess`, etc., based on the resources your CDK stack will deploy.
- Configure the trust relationship for the role to allow GitHub Actions to assume the role using OpenID Connect.

#### 2. Configuring GitHub Secrets

- In your GitHub repository settings, navigate to "Secrets" and add the following secrets:
  - `AWS_ROLE_ARN`: The ARN of the IAM role created in step 1.
  - `AWS_REGION`: The AWS region where your resources will be deployed.
  - `AWS_ACCOUNT_ID`: Your AWS account ID.

#### 3. Workflow Configuration

- Define GitHub Actions workflows in `.github/workflows` directory.
- `tests.yml`: Triggered on pull requests for running tests.
- `deployment.yml`: Used for deploying resources to AWS using CDK.

#### 4. CDK Deployment

- Implement your CDK stack in your preferred programming language (Python, TypeScript, etc.).
- Configure CDK to use the provided AWS role ARN and region from GitHub Secrets.
- Ensure your CDK code is version controlled in your GitHub repository.

### Usage

1. Push your CDK code changes to your GitHub repository.
2. GitHub Actions workflows will automatically trigger based on defined events (e.g., push, pull request).
3. The deployment workflow will authenticate with AWS using OIDC, assume the IAM role, and deploy your resources using CDK.
4. Monitor workflow runs in GitHub Actions to ensure successful deployment.

### Security Considerations

- Use fine-grained IAM policies to restrict access and permissions for GitHub Actions.
- Regularly review and audit IAM roles, policies, and permissions in your AWS account.
- Follow AWS security best practices and guidelines when configuring IAM roles and policies.

### Additional Resources

- [AWS CDK Documentation](https://docs.aws.amazon.com/cdk/latest/guide/home.html)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Configuring OpenID Connect in AWS](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services)

By following these steps and guidelines, you can set up a secure and automated deployment pipeline using GitHub Actions and AWS CDK.

# IMPORTANT NOTE

- This is a template so you need to enter correct information
