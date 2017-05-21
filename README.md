# friends-of-bash

Friends of Ba$h. A collection of useful bash functions. Easy to include in your bash scripts.

## 1.) First usage

### 1.1) installation & show version

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

### 1.2) show help

```
user$ friends-of-bash --help

Usage: /usr/local/bin/friends-of-bash [options...] {install|update|status}
 -h,    --help                    Shows this help.

 -v,    --version                 Shows the version number.

```

### 1.3) show status

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

### 1.4) update library

```
$ friends-of-bash update
```

## 2.) Usage

TODO: Describe the usage of this library here.

## 3.) Libraries

1. [array](docs/README-ARRAY.md)
2. [cert](docs/README-CERT.md)
3. [checker](docs/README-CHECKER.md)
4. [color](docs/README-COLOR.md)
5. [date](docs/README-DATE.md)
6. [device](docs/README-DEVICE.md)
7. [docker](docs/README-DOCKER.md)
8. [docker-container](docs/README-DOCKER-CONTAINER.md)
9. [docker-image](docs/README-DOCKER-IMAGE.md)
10. [domain](docs/README-DOMAIN.md)
11. [file](docs/README-FILE.md)
12. [filesystem](docs/README-FILESYSTEM.md)
13. [general](docs/README-GENERAL.md)
14. [git](docs/README-GIT.md)
15. [install](docs/README-INSTALL.md)
16. [json](docs/README-JSON.md)
17. [mail](docs/README-MAIL.md)
18. [network](docs/README-NETWORK.md)
19. [output](docs/README-OUTPUT.md)
20. [screen](docs/README-SCREEN.md)
21. [string](docs/README-STRING.md)
22. [system](docs/README-SYSTEM.md)
23. [version](docs/README-VERSION.md)

## License

MIT © [Björn Hempel](https://www.ixno.de)
# 
