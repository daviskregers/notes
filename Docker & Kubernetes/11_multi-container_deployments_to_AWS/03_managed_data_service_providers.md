# Managed Data Service providers

If you noticed, that `docker-compose.yml` file contains databases - `redis` and `postgres`, while `Dockerrun.aws.json` does not. This is made because it will use the `AWS Elastic Cache` and `AWS Relational Database` services.

The reason behind using amazon services instead of dockerized images are:
1. Automatically creates and maintains instances for you
2. Easy to scale
3. Built-in logging and maintenance
4. Probably better security than what we can do
5. Easier to migrate off  EB with
6. Automated backups and rollbacks


