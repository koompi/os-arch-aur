# HOW TO SETUP ARCHLINUX AUR BUILD 

### Setup environment for build AUR package

Before build aur package, you need set up environment such as fakeroot, create the repository database for build aur package. To setup all this environment you can follow this:

```
$ git clone https://github.com/koompi/os-arch-aur.git
$ cd os-arch-aur
$ sudo chmod +x setup && ./setup
```
`setup` *is bash script that use for setup environment for build AUR package.*

### Start build AUR package

Atfer you setup evironment for build AUR package already, now you can start build AUR package by using bash script `build`.  This script will check AUR package in file `package-list` and clone it, and then start build each AUR package. Atfer build already this script will add AUR package that build already to repository database,
You can follow this:

```
$ cd os-arch-aur
$ sudo chmod +x build && ./build
```

*Note: if you want host this custom repo to server, you can set up rsync for sync all AUR package and repository database to server.*  

### Setup rsync

You need to edit in file `build`  for setup rsync.

```
# uncomment line 146
rsync -av $PACKAGES/*.pkg.tar.xz username@[IP-Address]:[location-directory]
# uncomment line 149
rsync -av $(pwd)/local-repo/ username@[IP Address]:[localtion-directory]
```

*Note: `location-directory` is location path on server.*
