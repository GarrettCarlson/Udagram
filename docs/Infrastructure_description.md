# Infrastructure Descriptions
## DB
### AWS Relational Database Service (RDS)
The application DB requires a PostgreSQL server running in RDS.

* The DB must run PostgreSQL 12 or 13.
* The DB instance ID, master username and password may be configured arbitrarily.
* The **DB instance class** must be `Burstable` with minimal size e.g. `db.t3.micro`.
* The **Database name** and **Additional configuration/Initial database name** must be `postgres`.
* The DB **Connectivity/Public access** must be `yes`.
* The DB **Connectivity/Database port** must be `5432`.
* The DB security group inbound rules must allow `All traffic` from `0.0.0.0/0` with IP version `IPv4`.

## Frontend
### AWS Simple Storage Solution (S3)
The application frontend requires an S3 bucket set up for static web hosting.

* The bucket **Properties/Static website hosting** must be `enabled`.
* The bucket **Permissions/Access control list (ACL)** config must have `ACLs enabled` and `Bucket owner preferred`.
* The bucket **Permissions/Block all public access** must be `Off`
* The bucket name referenced in the frontend package deploy script `udagram\udagram-frontend\bin\deploy.sh` must be updated to match the infrastructure.
* The bucket **Bucket policy** must allow the s3.GetObject action on all Principals.
* The bucket **Cross-origin resource sharing (CORS)** configuration must allow `POST`, `GET`, `PUT`, `DELETE`, and `HEAD` methods on all `*` headers, from all `*` origins.


## API
### AWS Elastic Beanstalk (EB)
The API requires an EB instance in an EB environment configured for the Node.js 14+ platform.

* The EB instance must be created as a `single` instance with type `t2.medium`
* It is recommended to create this instance with an RSA key pair to connect via SSH for debugging.
* The following environment variables must be set in the EB environment:
1. AWS_BUCKET = {Amazon Resource Node (ARN) from your S3 bucket}
2. AWS_PROFILE = default
3. AWS_REGION = {AWS region selected while creating the EB environment}
4. JWT_SECRET = {JWT secret string - arbitrary}
5. POSTGRES_DB = `postgres`
6. POSTGRES_HOST = {AWS endpoint for the RDS DB, found under **Connectivity & security** in the RDS console for your RDS instance}
7. POSTGRES_USERNAME = {username for your PostgreSQL DB running on RDS}
8. POSTGRES_PASSWORD = {password for your PostgreSQL DB running on RDS}
* The `apiHost` referenced in the `./udagram/udagram-frontend/src/environments/*.ts` files must be updated to match the EB endpoint.
Reference `./udagram/udagram-api/.elasticbeanstalk/config.yml` for additional details.