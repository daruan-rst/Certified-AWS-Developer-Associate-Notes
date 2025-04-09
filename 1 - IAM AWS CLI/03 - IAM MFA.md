# IAM Password Policy
 - The stronger the password, the higher security your account has
 - In AWS it is possible to set up a password policy with diferent options:
    - Minimum password length
    - Require specific character types:
        - Uppercase letters
        - Lowercase letters
        - Numbers
        - Non-alphabetic characters
    - Allow all IAM users to change their own passwords
    - Require users to change their password after a specified period of time (password expiration)
    - Prevent password reuse

## Multifactor Authentication (MFA)
- We protect out root accounts and IAM users with an MFA device in order to prevent important AWS resources from being deleted or altered
- A MFA is a combination of:
    - Password you know
    - Security device you own
- MFA devices options in AWS:
    - Virtual MFA device:
        - Google authenticator (phone only)
        - Authy (multi-device)
    - Universal 2nd factor (U2F) security key
        - Physical device
            - Ex: Yubikey by Yubico
    - Hardware key Fab MFA device
        - Ex: Gemalto