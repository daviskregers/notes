# AWS Cognito

- We want to give our users an identity so that they can interact with our application

## Cognito User Pools

- Sign in functionality for app users
- Integrate with [[AWS API Gateway]]
- Create a [[Serverless]] database of users for your mobile apps
- Simple login: username (or email) and password combination
- Can enable Federated Identities (facebook, Google, [[SAML]])
- Sends back [[JSON Web Tokens (JWT)]]
- Can be integrated with [[AWS API Gateway]] for [[authentication]]

## Cognito Identity Pools (Federated Identity)

- Provide AWS credentials to users so they can access AWS resources directly
- Integrate with Cognito User Pools as an identity provider
- Goal
	- Provide direct access to AWS Resources from the Client Side
- How
	- Log in to federated identity provider - or remain anonymous
	- Get temporary AWS credentials back from the Federated Identity Pool
	- These credentials come with a pre-defined IAM policy stating their permissions
- Example
	- provide (temporary) access to write to [[S3]] bucket using Facebook Login

## Cognito Sync

- Deprecated - use [[11-appsync]] now
- Store preferences, configuration, state of app
- Cross device synchronization (any platform - iOS, Android, etc)
- Offline capability (synchronization when back online)
- Requires Federated Identity Pool in [[Programming/AWS/solutions-architect-associate/12-serverless-overviews-from-a-solution-architect-perspective/AWS Cognito]] (not User Pool)
- Store data in datasets (up to 1MB)
- Up to 20 datasets to synchronise
