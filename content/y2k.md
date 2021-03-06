---
title: "Y2K"
menu: main
---

The tcsh code has been tested on a Solaris 2.6 machine and a NetBSD 1.3H
machine running before, and after the year 2000. The code has been also
visually inspected for Y2K compliance problems. Tcsh does not use time
functions for anything but display purposes, so its operation should not
be affected assuming that the time related functions of the C library
work properly.

**Note:** Since the last audit, tcsh-6.08.00 has been found to have a
minor problem with `%y` in the prompt (it will print `10` instead of
`00` in y2k). This has been fixed in tcsh-6.09.00.
