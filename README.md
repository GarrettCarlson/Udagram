# Udagram
Udagram is a social networking application for sharing photos.

## Screenshot of Working Application
![Working Application](/screenshots/working_application.jpg?raw=true)

## Screenshots of Last successful CircleCi build
### Build
![CircleCi Build](/screenshots/circleci_build.jpg?raw=true)

### Hold
![CircleCi Hold](/screenshots/circleci_hold.jpg?raw=true)

### Deploy
![CircleCi Build](/screenshots/circleci_deploy.jpg?raw=true)

##  AWS RDS for the database overview
![AWS RDS](/screenshots/aws_rds_overview.jpg?raw=true)

##  AWS ElasticBeanstalk for the (backend) API deployment
![AWS ElasticBeanstalk API](/screenshots/aws_eb_overview.jpg?raw=true)

##  AWS S3 for (frontend) web hosting
![AWS S3 Frontend](/screenshots/aws_s3_overview.jpg?raw=true)

## Link to the Hosted Application
http://myawsbucket-1234509823456.s3-website-us-east-1.amazonaws.com/

## CircleCI Secrets Management
Secrets are configured in CircleCI through environment variables and are not present in the source code.
![CircleCI Secrets](/screenshots/circleci_secrets.jpg?raw=true)

### Dependencies

```
- Node v14.15.1 (LTS) or more recent. While older versions can work it is advisable to keep node to latest LTS version

- npm 6.14.8 (LTS) or more recent, Yarn can work but was not tested for this project

- AWS CLI v2, v1 can work but was not tested for this project

- A RDS database running Postgres.

- A S3 bucket for hosting uploaded pictures.

```

### Installation

Provision the necessary AWS services needed for running the application:

1. In AWS, provision a publicly available RDS database running Postgres.
1. In AWS, provision a s3 bucket for hosting the uploaded files.
1. Export the ENV variables needed or use a package like [dotnev](https://www.npmjs.com/package/dotenv)/.
1. From the root of the repo, navigate udagram-api folder `cd starter/udagram-api` to install the node_modules `npm install`. After installation is done start the api in dev mode with `npm run dev`.
1. Without closing the terminal in step 1, navigate to the udagram-frontend `cd starter/udagram-frontend` to intall the node_modules `npm install`. After installation is done start the api in dev mode with `npm run start`.

## Testing

This project contains two different test suite: unit tests and End-To-End tests(e2e). Follow these steps to run the tests.

1. `cd starter/udagram-frontend`
1. `npm run test`
1. `npm run e2e`

There are no Unit test on the back-end

### Unit Tests:

Unit tests are using the Jasmine Framework.

### End to End Tests:

The e2e tests are using Protractor and Jasmine.

## Built With

- [Angular](https://angular.io/) - Single Page Application Framework
- [Node](https://nodejs.org) - Javascript Runtime
- [Express](https://expressjs.com/) - Javascript API Framework

## License

[License](LICENSE.txt)
