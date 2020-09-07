# HOW TO SETUP AUTO BUILD AUR PACKAGE 

### Resolve dependencies.

Add the repo to `/etc/pacman.conf` for resolve dependencies.

```
[koompi]
SigLevel = Never
Server = https://repo.koompi.org/kmp-apps
```

### Setup environment for build AUR package

Before build aur package, you need set up environment such as fakeroot, create the repository database for build aur package. To setup all this environment you can follow this:

```
$ git clone https://github.com/koompi/os-arch-aur.git
$ cd os-arch-aur
$ sudo chmod +x setup && ./setup
```
`setup` : *is bash script that use for setup environment for build AUR package.*

### Set up rsync server repo
```
cp .server-example .server
nano .server
```
- IPADDRESS=SERVER
- USERNAME=USERNAME
- PASSWORD=PASSWORD
- PATHREPO=PATHSERVER

### Start build AUR package

Atfer you setup evironment for build AUR package already, now you can start build AUR package by using bash script `build`.  This script will check AUR package in file `package-list` and clone it, and then start build each AUR package. Atfer build already this script will add AUR package that build already to repository database,
You can follow this:

```
$ cd os-arch-aur
$ sudo chmod +x build && ./build
```

*Note: if you want host this custom repo to server, you can set up rsync for sync all AUR package and repository database to server.*  

### AURsync

For `aursync` to work, we need to add a repository to `/etc/pacman.conf`

```
[reponame]
SigLevel = Never
Server = https://IP-server/repo/x86_64/