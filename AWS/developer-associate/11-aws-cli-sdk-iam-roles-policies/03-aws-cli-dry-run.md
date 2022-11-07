# AWS CLI Dry Runs

- Sometimes, we'd just like to make sure we have the permissions but not actually run the commands

- Some AWS CLI commands (such as EC2) can become expensive if they succeed, say if we wanted to try to create an EC2 Instance
- Some AWS CLI commands (not all) contain a --dry-run option to simulate API calls

```console
$ aws ec2 run-instances --dry-run --image-id ami-06340c8c12baa6a09 --instance-type t2.micro

An error occured (UnauthorizedOperation) when calling the RunInstances operation: You are not authorized to perform this operation. Encoded authorization failure message: ...
```

When we set the RunInstances permissions:

```console
$ aws ec2 run-instances --dry-run --image-id ami-06340c8c12baa6a09 --instance-type t2.micro

An error occurred (DryRunOperation) when calling the RunInstances operation: Request would have succeeded, but DryRun flag is set.
```