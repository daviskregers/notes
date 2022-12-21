---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: tool
Source: https://httpie.io/
Tags: [development/tools/testing, review]
sr-due: 2023-04-24
sr-interval: 145
sr-ease: 250
---

Httpie is an API testing tool, similar to [[Postman]] but it also includes a command line version as well.

## Installing

### Mac

```console
brew install httpie
```

### Ubuntu / Debian

```console
apt install httpie
```

### Archlinux

```console
pacman -S httpie
```


## Usage

You can refer to documentation [here](https://httpie.io/docs/cli/usage).
Basically, you can use:

```console
$ http PUT pie.dev/put X-API-Token:123 name=John
```
