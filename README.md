# friends-of-bash

Friends of Ba$h. A collection of useful bash functions. Easy to include in your bash scripts.

## 1.) First usage

### 1.1) Installation & show version

```
user$ cd ~ && git clone git@github.com:bjoern-hempel/friends-of-bash.git && cd friends-of-bash
user$ sudo -E bin/install
user$ cd .. && rm -rf friends-of-bash
user$ friends-of-bash --version
friends-of-bash/v0.0.51
```

### 1.2) Show help

```
user$ friends-of-bash --help

"friends of bash": A bash function library (v0.0.51) by Björn Hempel <bjoern@hempel.li>.

Usage: /usr/local/bin/friends-of-bash [options...] {install|status|update|version|list|updateAvailable|osName}
 -y,    --yes                     Auto yes. Don't answer to update questions.

 -s,    --short                   Try to shorten the output.

 -r,    --remote                  Do a remote check.

 -h,    --help                    Shows this help.

 -v,    --version                 Shows the version number.
```

### 1.3) Show status

#### 1.3.1) Single application

```
user$ friends-of-bash status 

friends-of-bash
---------------

Currently installed version:   v0.0.51
Available version:             v0.0.51

Currently installed changeset: 2e86d582411c2df92ddefb0acd41e0bc5cd0a01b
Available changeset:           2e86d582411c2df92ddefb0acd41e0bc5cd0a01b

Your "/opt/friends-of-bash/friends-of-bash" version is up to date. Nothing to do here.
```

```
user$ friends-of-bash status apache-host-viewer

apache-host-viewer
------------------

Currently installed version:   v0.0.40
Available version:             v0.0.40

Currently installed changeset: 674c4a6854c45d73bdfa1f43a077f1b5d538449f
Available changeset:           674c4a6854c45d73bdfa1f43a077f1b5d538449f

Your "/opt/friends-of-bash/apache-host-viewer" version is up to date. Nothing to do here.
```

#### 1.3.2) All applications

```
user$ friends-of-bash status all
apache-host-viewer - apache-host-viewer/v0.0.39 - new version is available (v0.0.40)
backup-mysql - backup-mysql/v0.0.3 - application is up to date
friends-of-bash - friends-of-bash/v0.0.51 - application is up to date
hello-world - hello-world/v1.0.8 - application is up to date
project-analyser - project-analyser/v0.0.10 - application is up to date (Attention: 3 changed files found!)
service-checker - service-checker/v0.0.18 - application is up to date (Attention: 1 changed files found!)
```

### 1.4) Update library

#### 1.4.1) Single application

##### 1.4.1.1) Example I

```
user$ friends-of-bash update apache-host-viewer
```

##### 1.4.1.2) Example II

```
user$ cd /opt/friends-of-bash/apache-host-viewer
user$ friends-of-bash update .
```

#### 1.4.2) All applications

```
user$ friends-of-bash update all
```

#### 1.4.3) Don't ask. Update immediately (`-y`)

```
user$ friends-of-bash update all -y
```

### 1.5) Show os name and version

```
$ friends-of-bash osName
```

## 2.) Manage other repositories

### 1.1) Installation & show version

Use the parameter -E to pass through your ssh private key while doing a `sudo git clone`:

```
user$ sudo -E friends-of-bash install "git@github.com:bjoern-hempel/apache-host-viewer.git"
```

or

```
user$ sudo -E friends-of-bash install "git@github.com:bjoern-hempel/hello-world.git"
```

With this technique you can install any git repository you want to. After installation via `friends-of-bash install` you can do the versioning handling with the friends-of-bash helper (see next chapters). Showing the version numbers:

```
user$ friends-of-bash version apache-host-viewer
apache-host-viewer/v0.0.2
```

or

```
user$ friends-of-bash version hello-world
hello-world/v1.0.0
```

All installed repositories you will find below the directory `/opt/friends-of-bash`. The installer will execute an install file (if exists). The install file must be located directly within the root folder of your repository by the name of `install`. Alternatively you can create an `install` folder with some symlinks linked to existing files within your repository. They all will be installed at `/usr/local/bin`. Go here https://github.com/bjoern-hempel/apache-host-viewer/tree/master/install to see an example that will create a symlink like this:

```
user$ ls -l /usr/local/bin/.
insgesamt 12
lrwxrwxrwx 1 root staff  62 Jun  4 20:01 apache-host-viewer -> /opt/friends-of-bash/apache-host-viewer/bin/apache-host-viewer
...
```

You can execute the above mentioned symlink `apache-host-viewer` from anywhere you want to like this:

```
user$ apache-host-viewer --version
apache-host-viewer/v0.0.2
```

### 1.2) list all packages installed via `friends-of-bash install`

```
user$ friends-of-bash list
apache-host-viewer - apache-host-viewer/v0.0.2
backup-mysql - backup-mysql/v0.0.1
friends-of-bash - friends-of-bash/v0.0.14
hello-world - hello-world/v1.0.0
```

### 1.3) Show status

```
user$ friends-of-bash status apache-host-viewer

apache-host-viewer
------------------

Currently installed version:   v0.0.2
Available version:             v0.0.2

Currently installed changeset: dcb2217b4081bc1124568545ddd6f58e76325191
Available changeset:           dcb2217b4081bc1124568545ddd6f58e76325191

Your "/opt/friends-of-bash/apache-host-viewer" version is up to date. Nothing to do here.
```

### 1.4) Update library

#### 1.4.1) Individual

```
user$ friends-of-bash update apache-host-viewer
```

#### 1.4.2) All libraries

```
user$ friends-of-bash update all
```

### 1.5) Update version number

#### 1.5.1) Increase the revision number

```
user$ friends-of-bash updateVersion apache-host-viewer
```

#### 1.5.2) Increase the minor number

TODO

#### 1.5.3) Increase the major number

TODO

## 3.) Usage

TODO: Describe the general usage of this library here.

## 4.) Libraries

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
