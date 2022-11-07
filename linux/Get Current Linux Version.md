# Get current linux version

## Get kernel version

```
uname -a
```

```
Linux davis-mint 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

```
cat /proc/version
```

```
Linux version 4.15.0-20-generic (buildd@lgw01-amd64-039) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018
```

## Get distribution version

```
cat /etc/*release
```

```
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=19
DISTRIB_CODENAME=tara
DISTRIB_DESCRIPTION="Linux Mint 19 Tara"
NAME="Linux Mint"
VERSION="19 (Tara)"
ID=linuxmint
ID_LIKE=ubuntu
PRETTY_NAME="Linux Mint 19"
VERSION_ID="19"
HOME_URL="https://www.linuxmint.com/"
SUPPORT_URL="https://forums.ubuntu.com/"
BUG_REPORT_URL="http://linuxmint-troubleshooting-guide.readthedocs.io/en/latest/"
PRIVACY_POLICY_URL="https://www.linuxmint.com/"
VERSION_CODENAME=tara
UBUNTU_CODENAME=bionic
cat: /etc/upstream-release: Is a directory
```