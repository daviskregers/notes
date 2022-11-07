# IAM Policies Hands On

If we remove the previously made user from the admin group, we would see a following error when viting the IAM page.

![iam-permission-needed](iam-permission-needed.png)

We are going to create a new group `developers` and attach the a random permission to it like `AWSDirectConnectReadOnlyAccess`, attach the user to it.
We are going to re-attach the user to the `admin` group.
We are going to add permission straight to the user:

![iam-add-permission](iam-add-permission.png)

![iam-attach-policy](iam-attach-policy.png)

Now we can see that the user has 3 policies - one attached directly, one from admin group and one from the developers group.

![iam-policies-inherited](iam-policies-inherited.png)

---

If we go to the policy section, open one up and click on the `JSON` button, we can see that these policies are written
in the format we previously looked at:

![administrator-policy](administrator-policy.png)

![iam-readonly-policy](iam-readonly-policy.png)

---

You can also create your own policies which can be done either with a simple JSON or a visual editor.

![create-policy-json](create-policy-json.png)

![create-policy-visual-editor](create-policy-visual-editor.png)

![policy-ve-filled](policy-ve-filled.png)

If we click back to the `JSON`, it will be populated:

![filled-policy-json](filled-policy-json.png)
