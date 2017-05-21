# friends-of-bash

Friends of Ba$h. A collection of useful bash functions. Easy to include in your bash scripts.

## A.) First usage

### A.1) installation & show version

```
user$ cd ~
user$ git clone git@github.com:bjoern-hempel/friends-of-bash.git
user$ cd friends-of-bash
user$ sudo ./install
user$ cd ..
user$ rm -rf friends-of-bash
user$ friends-of-bash --version
friends-of-bash/v0.0.5 (04b96992e3623e1270496fa04d0fe6dc6cc9a9f2)
```

### A.2) show help

```
user$ friends-of-bash --help

Usage: /usr/local/bin/friends-of-bash [options...] {install|update|status}
 -h,    --help                    Shows this help.

 -v,    --version                 Shows the version number.

```

### A.3) show status

```
$ friends-of-bash status

friends-of-bash

Currently installed version:   v0.0.5
Available version:             v0.0.6

Currently installed changeset: 04b96992e3623e1270496fa04d0fe6dc6cc9a9f2
Available changeset:           67f7aade0275f01037b531764b1cc2e75b63ce45

Your friends of bash library version is not up to date. Please update with:
user$ /usr/local/bin/friends-of-bash update
```

