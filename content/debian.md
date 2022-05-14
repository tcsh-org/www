---
title: "Debian and Ubuntu"
menu:
  main:
    name: Deb
---

To install packages from the TCSH repository for Debian and Ubuntu,
you should first download a trust anchor into your system using this
command:

```
curl -o /usr/share/keyrings/tcsh-archive-keyring.gpg \
    https://deb.tcsh.org/tcsh-archive-keyring.gpg
```

Then create the configuration that adds the repository to the sources
used by `apt`:

```
echo 'deb [signed-by=/usr/share/keyrings/tcsh-archive-keyring.gpg]' \
    https://deb.tcsh.org/`lsb_release -is | tr A-Z a-z`/ \
    `lsb_release -cs` main > /etc/apt/sources.list.d/tcsh.list

```

Once this is done, you can update `tcsh` to the latest available version.

```
apt-get update && apt-get install tcsh
```

Finally make sure updates to the keyring are received in a timely manner.

```
apt-get install tcsh-archive-keyring
```

Packages are available for the following operating system releases:

* Debian 11 (bullseye)
* Debian 10 (buster)
* Debian 9 (stretch)
* Ubuntu 22.04 (jammy)
* Ubuntu 21.10 (impish)
* Ubuntu 20.04 (focal)
* Ubuntu 18.04 (bionic)

Packages are available for the `amd64` and `arm64` architectures only.
