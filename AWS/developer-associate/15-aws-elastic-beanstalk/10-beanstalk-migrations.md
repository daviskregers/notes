# Beanstalk Migrations

- After creating an Elastic Beanstalk environment, you cannot change the Elastic Load Balancer type (only the configuration).
- To migrate:
1. Create a new environment with the same configuration except LB (can't clone)
2. Deploy your application onto the new environment
3. Perform a CNAME swap or Route 53 update

## RDS with Elastic Beanstalk

- RDS can be provisioned with Beanstalk which is great for dev / test
- This is not great for production as the database lifecycle is tied to the beanstalk environment lifecycle
- The best for prod is to separately create an RDS database and provide our EB application with the connection string

## Decouple RDS

- Create a snapshot of RDS DB (as a safeguard)
- Go to the RDS console and protect the RDS database from deletion
- Create a new Elastic Beanstalk environment, without RDS, point your application to existing RDS
- Perform a CNAME swap (blue/green) or route 53 update, confirm working
- Terminate the old environment (RDS won't be deleted)
- Delete CloudFormation stack in DELETE_FAILED state