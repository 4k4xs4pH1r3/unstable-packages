# Install Offensive Security Tools in Termux

[![Powered by JFrog Bintray](./.github/static/powered-by-bintray.png)](https://bintray.com)

There are located packages which were requested, but not added to the
[main][termux-packages] Termux repository due to various reasons. Packages
available here may have lower quality, be unstable or not work at all.

## 1. Pepare

Execute this:

```ShellSession
export PATH=/sbin:/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin && export PATH=$PATH:/usr/local/sbin:/usr/local/bin && sudo apt-get update -y && cd /var/cache/debconf && rm *.dat
```

## 2. Install:
```ShellSession
pkg install unstable-repo root-repo x11-repo -y && pkg install neofetch coreutils busybox screenfetch metasploit python python2 ruby git php perl nmap bash clang nano figlet cowsay curl tar zip unzip tor tsu wget wcalc openssl bmon -y && pkg update -y && pkg upgrade -y && cp $(which pip) $PREFIX/bin/pip3 && neofetch 
```
## Building packages manually

You can build all packages manually by using provided docker image. The only
requirements are Linux-based host with Docker installed.

1. Clone this repository:
	```ShellSession
	git clone https://github.com/termux/unstable-packages
	```

2. Enter build environment (will download docker image if necessary):
	```ShellSession
	cd ./unstable-packages
	./start-builder.sh
	```
	Command shown above will start builder for Android 7 (API level 24). If you
	need to build package for Android 5, use `./start-builder-legacy.sh`.

3. Choose package you want to build and run:
	```ShellSession
	./build-package.sh -a ${arch} ${package name}
	```
	Replace `${arch}` with target CPU architecture and `${package name}` with
	package name you want to build.

## Contributing

If you wish to contribute, please take a look on our [contributing guide](./CONTRIBUTING.md).

[termux-packages]: <https://github.com/termux/termux-packages>
