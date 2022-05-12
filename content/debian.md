---
title: "Debian Repository"
menu:
  main:
    name: Debian
---

To install packages from the TCSH repository for Debian, you should
first download a trust anchor into your system using this command:

```
curl -O /usr/share/keyrings/tcsh-archive-keyring.gpg \
    https://deb.tcsh.org/debian/tcsh-archive-keyring.gpg
```

Then download the configuration for adding the repository to the sources
used by `apt`:

```
curl -O /etc/apt/sources.list.d/tcsh.list \
    https://deb.tcsh.org/debian/tcsh.list
```

Once this is done, you can run `apt-get update` for the changes to take
effect and use `apt-get install tcsh-archive-keyring` to make sure
updates to the keyring are received in a timely manner.
