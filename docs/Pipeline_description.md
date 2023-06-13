# Pipeline Description
*Refer to `.circleci/config.yml` and `package.json/scripts{}` for details.*
## Build
* Uses Node 14.15, using npm as the package manager.
1. Installs frontend dependencies.
2. Installs API dependencies.
3. Lints frontend code.
4. Builds frontend code.
5. Builds API code.

## Hold
* After building, the pipeline will hold until approval before moving on to the next step - Deploy.

## Deploy
1. Runs setup for AWS Elastic Beanstalk (EB).
2. Runs setup for AWS CLI.
3. Checks out master branch from GitHub.
4. Deploys API build code using `eb deploy`.
5. Deploys frontend build code using `.udagram/udagram-frontend/bin/deploy.sh`, which uses `aws s3` to deploy to AWS Simple Storage Service (S3) bucket defined in the script.