# AWS CLI STS Decode Errors

- When you run API calls and they fail, you can get a long error message
- This error message can be decoded using the STS command line
- sts decode-authorization-message

```console
$ aws sts decode-authorization-message --encoded-message ...

An error orcurred (AccessDenied) when calling the DecodeAuthorizationMessage operation: User: arn:aws:sts:123:assumed-role/MyFirstEC2Role/i-05adcce6933809eda is not authorized to perform: sts:DecodeAuthorizationMessage
```

If this happens, we need to add the STS DecodeAuthorizationMessage policy to the role.

```json
{
    "DecodedMessage": "..."
}
```