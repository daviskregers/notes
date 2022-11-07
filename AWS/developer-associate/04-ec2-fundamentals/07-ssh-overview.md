# SSH Overview

The SSH is used to connect to the cloud instances to perform maintenance or other actions.

Depending on your operating system, there can be several ways to connect to the instance:

|               | SSH | Putty | EC2 Instance Connect |
|---------------|-----|-------|----------------------|
| Mac           | +   |       | +                    |
| Linux         | +   |       | +                    |
| Windows < 10  |     | +     | +                    |
| Windows >= 10 | +   | +     | +                    |

## SSH using linux or mac

1. Get the public IP of the instance
2. Make sure in the inbound rules that the port 22 is open and the source can be from your IP address.
3. Locate the PEM key you downloaded when the instance was created
4. Ssh into your instance:

```bash
ssh -i EC2Tutorial.pem ec2-user@PUBLIC-IP
```

If there is an error saying `Permissions 0644 for 'EC2Tutorial.pem' are too open` - you need to change the key permissions.

```bash
chmod 0400 EC2Tutorial.pem
```

## SSH using windows

You can configure all the required parameters necessary for doing SSH on windows using the free tool called [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/).

1. Install Putty
2. Open up a program called `PuttyGen` or `Putty Key Generator` to convert the PEM key file to PPK.
    - Click on `File -> Load private key` and select the PEM file. (make sure that the file type filter is selected to All Files).
    - Set a password if wanted
    - Click on `save private key`
3. Open up `Putty`
    - Under the host name enter `ec2-user@PUBLIC-IP-ADDRESS`
    - Save it under the saved sessions
    - On the left side pane we go to `Connection -> SSH -> Auth`, there will be an option to choose a private keyfile for authentication - use the previously generated key.
    - Save the profile once more
    - Click on open

## SSH using windows 10

1. Open up PowerShell/cmd and type `ssh` - it should return a usage documentation. If it does - you can proceed. If not - use putty.
2. Locate the PEM key you downloaded when the instance was created
4. Ssh into your instance:

```bash
ssh -i C:\Users\Davis\Downloads\Ec2Tutorial.pem EC2Tutorial.pem ec2-user@PUBLIC-IP
```

If there is an error saying `Permissions 0644 for 'EC2Tutorial.pem' are too open` - you need to change the key permissions.

You can do that by right-clicking on the file `Properties -> Security -> Advanced`.
- The owner of the key should be you.
- Disable inheritance
- Remove any other users