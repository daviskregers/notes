# Kubernetes security with RBAC

`RBAC` stands for `Role Based Access Control`:
- Limits who can access and modify objects in our cluster
- Enabled on Google Cloud by default
- Tiller wants to make changes to our cluster, so it needs to get some permissions set

There are 4 different security roles:
- `User Accounts` - identifies as a `person` administering our cluster
- `Service Accounts` - identifies a `pod` administering a cluster
- `ClusterRoleBinding` - Authorizes an account to do a certain set of actions accros the entire cluster
- `RoleBinding` - Authorizes an account to do a certain set of actions in a single namespace.

