# friends-of-bash

Friends of Ba$h. A collection of useful bash functions. Easy to include in your bash scripts.

## 0.) Requirements

You need bash with version 4 at least, because it supports associative arrays and other stuff (https://www.admon.org/scripts/new-features-in-bash-4-0/):

```bash
user$ bash --version
GNU bash, Version 4.4.12(1)-release (x86_64-pc-linux-gnu)
Copyright (C) 2016 Free Software Foundation, Inc.
...
```

If you have a version lower than the version 4 (for example on mac):

```bash
user$ bash --version
GNU bash, version 3.2.57(1)-release (x86_64-apple-darwin17)
Copyright (C) 2007 Free Software Foundation, Inc.
```

You have to update your bash version first.

### 0.1) Update bash on mac to version 4

```bash
user$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
user$ brew update && brew install bash
```

Reopen your terminal and check again:

```bash
user$ bash --version
GNU bash, Version 4.4.19(1)-release (x86_64-apple-darwin17.3.0)
Copyright (C) 2016 Free Software Foundation, Inc.
...
```

Add the new shell to the list of allowed shells:

```
user$ sudo bash -c 'echo /usr/local/bin/bash >> /etc/shells'
```

Change the shell:

```
user$ chsh -s /usr/local/bin/bash
```

Check the used shell locations:

```
user$ which -a bash
/usr/local/bin/bash
/bin/bash
```

Looks good. Now you are ready to use this library on your mac as well.

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

### 1.4) Update friends-of-bash library

```
user$ friends-of-bash update
```

### 1.5) Show os name and version

```
user$ friends-of-bash osName
```

## 2.) Manage other repositories

### 2.1) Installation & show version

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

### 2.2) list all packages installed via `friends-of-bash install`

#### 2.2.1) Full output

```
user$ friends-of-bash list
apache-host-viewer - apache-host-viewer/v0.0.40
backup-mysql - backup-mysql/v0.0.3
friends-of-bash - friends-of-bash/v0.0.51
hello-world - hello-world/v1.0.8
project-analyser - project-analyser/v0.0.10
service-checker - service-checker/v0.0.18
```

#### 2.2.2) Short output

```
user$ friends-of-bash list --short
apache-host-viewer/v0.0.40
backup-mysql/v0.0.3
friends-of-bash/v0.0.51
hello-world/v1.0.8
project-analyser/v0.0.10
service-checker/v0.0.18
```

### 2.3) Show status

#### 2.3.1) From a single application

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

#### 2.3.2) From all applications

```
user$ friends-of-bash status all
apache-host-viewer - apache-host-viewer/v0.0.39 - new version is available (v0.0.40)
backup-mysql - backup-mysql/v0.0.3 - application is up to date
friends-of-bash - friends-of-bash/v0.0.51 - application is up to date
hello-world - hello-world/v1.0.8 - application is up to date
project-analyser - project-analyser/v0.0.10 - application is up to date (Attention: 3 changed files found!)
service-checker - service-checker/v0.0.18 - application is up to date (Attention: 1 changed files found!)
```

### 2.4) Update friends-of-bash application

#### 2.4.1) Individual (Example I)

```
user$ friends-of-bash update apache-host-viewer
```

#### 2.4.2) Individual (Example II)

```
user$ cd /opt/friends-of-bash/apache-host-viewer
user$ friends-of-bash update .
```

#### 2.4.3) Update all applications

```
user$ friends-of-bash update all
```

#### 2.4.4) Don't ask. Update immediately (`-y`)

```
user$ friends-of-bash update all -y
```

### 2.5) Update version number

#### 2.5.1) Increase the revision version number in general

This technique works with each friends-of-bash application.

```
user$ cd /opt/friends-of-bash/friends-of-bash
user$ friends-of-bash updateVersion .
name:            friends-of-bash
directory:       /opt/friends-of-bash/friends-of-bash
current version: v0.0.51

Which new version number do you want to use? (1) - v1.0.0, (2) - v0.1.0 or (3) v0.0.52

Choose (1), (2) or (3): 3

This will set the current version number v0.0.51 to v0.0.52. Do you want to continue? Type (y)es or (no): y
```

#### 2.5.2) Increase the revision number

You will ask for. Please have a look at: "**2.5.1) Increase the revision version number in general**" (`friends-of-bash updateVersion`)

#### 2.5.3) Increase the minor number

You will ask for. Please have a look at: "**2.5.1) Increase the revision version number in general**" (`friends-of-bash updateVersion`)

#### 2.5.4) Increase the major number

You will ask for. Please have a look at: "**2.5.1) Increase the revision version number in general**" (`friends-of-bash updateVersion`)

## 3.) Usage

TODO: Describe the general usage of this library here. A basic usage application using this libraries you will find here: https://github.com/bjoern-hempel/hello-world

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
