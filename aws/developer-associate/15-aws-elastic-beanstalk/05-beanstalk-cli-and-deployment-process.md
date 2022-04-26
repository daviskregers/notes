# Elastic Beanstalk CLI

- We can install an additional CLI called the "EB cli" which makes working with Beanstalk from the CLI easier.
- Basic commands are:
    - eb create
    - eb status
    - eb health
    - eb events
    - eb logs
    - eb open
    - eb deploy
    - eb config
    - eb terminate
- It's helpful for your automated deployment pipelines!

## Elastic Beanstalk Deployment Process

- Describe dependencies (requirements.txt for python, package.json for Node.js)
- Package code as zip, and describe dependencies
    - Python: requirements.txt
    - Node.js: package.json
- Console: upload zip file (creates new app version), and then deploy
- CLI: create new app version using CLI (uploads zip), then deploy

- Elastic Beanstalk will deploy the zip on each EC2 instance, resolve dependencies and start the application