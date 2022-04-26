# Elastic Beanstalk Extensions

- A zip file containing our code must be deployed to Elastic Beanstalk
- All parameters set in the UI can be configured with code using files
- Requirements:
    - in the .ebextensions/ directory in the root of source code
    - YAML / JSON format
    - .config extensions (example logging.config)
    - Able to modify some default settings using option_settings
    - Ability to add resources such as RDS, ElastiCache, DynamoDB, etc
- Resources managed by .ebextensions get deleted if the environment goes away.

We can add an `.ebextensions/environment-variables.config` file:

```yml
# You must place this file in .ebextensions
# And must have a .config file name
# So the file is at .ebextensions/environment-variables.config
# Note: Even though the markup language is YAML, you must use .config extension

option_settings:
    # see: https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/command-options-general.html#command-options-general-elasticbeanstalkapplicationenvironment
    aws:elasticbeanstalk:application:environment:
        DB_URL: "jdbc:postgresql://rds-url-here.com/db"
        DB_USER: username

# This format works too:
# option_settings:
#     - namespace: namespace
#       option_name: option_name
#       value: option value
# See: https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/ebextensions-optionsettings.html
```