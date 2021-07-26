# IAM MFA overview

In order to protect our users and groups from being compromised we can utilize 2 defense mechanisms:

- Password Policy
    - Strong passwords = better security
    - Set minimum password length
    - Require specific character types
        - Including uppercase letters
        - lowercase letters
        - numbers
        - non-alphanumeric characters
    - Allow all IAM users to change their own passwords
    - Require users to change their passwords after some time (password expiration)
    - Prevent password re-use
- Multi Factor Authentication - MFA
    - MFA = password you know + security device you own
    - You can have several MFA device options in AWS like:
        - Virtual MFA device
            - Google Authenticator
            - Authy
        - Universal 2nd Factor (U2F) Security Key
            - YubiKey
        - Hardware Key Fob MFA Device
            - Gemalto
        - Hardware Key Fob MFA Device for AWS GovCloud (US)
            - SurePassID
