# IAM introduction: Users, Groups, Policies

- IAM stands for Identity And Access Management
- It is a global service

- Root account is created by default, shouldn't be used or shared.
- Users are people within your organization and can be grouped
- Groups can only contain users not other groups. Users can belong to multiple groups though.

- Groups are being created because:
    - You can create JSON documents called policies and assign them to groups or users.
    - These policies define the permissions of the users
    - In AWS you apply the least privilege principle: don't give more permissions than a user needs.

