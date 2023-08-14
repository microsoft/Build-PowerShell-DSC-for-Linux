# Build Powershell DSC (Desired State Configuration) for Linux
The primary purpose of this project is to build universal Linux .rpm and .deb packages for distribution.
The ULinux build of [Powershell DSC for Linux](https://github.com/Microsoft/PowerShell-DSC-for-Linux) is built upon the OMI, PAL and the ostc-openssl projects.

If local or development builds are desired, please follow the instructions in the README.md from the [Powershell DSC for Linux](https://github.com/Microsoft/PowerShell-DSC-for-Linux) project.
### Configuration:

To prepare your build system you must read and follow the steps below from the Build-omi project:

- [Glossary of Terms](https://github.com/Microsoft/Build-omi#glossary-of-terms)
- [Setting up a machine to build OMI](https://github.com/Microsoft/Build-omi#setting-up-a-machine-to-build-omi)
  - [Dependencies to build a native package](https://github.com/Microsoft/Build-omi#dependencies-to-build-a-native-package)
  - [Setting up a system to build a universal package](https://github.com/Microsoft/Build-omi#setting-up-a-system-to-build-a-universal-package)
  - [Setting up your system for git](https://github.com/Microsoft/ostc-docs/blob/master/setup-git.md)

DSC also requires curl and the curl development packages:
- RHEL, CentOS : 
```
sudo yum install curl libcurl-devel
```
- SLES: 
```
sudo zypper install curl libcurl-devel
```
- Debian/Ubuntu: 
 There are several back-ends for libcurl-dev.  The `apt-get` will list the candidates.  Pick the appropriate one to install.
```
sudo apt-get install curl libcurl-dev 
```

### Clone repository
 To clone the repository to build PowerShell-DSC-for-Linux, issue the following command:

```
git clone --recursive git@github.com:Microsoft/Build-Powershell-DSC-for-Linux.git bld-dsc
```

After this, you need to make sure that you're on the master branch for each
of the subprojects. To do this, issue the following commands:

```
cd bld-dsc
git checkout master
git submodule foreach git checkout master
```

You can also use an alias like ```git co-master``` if you followed 
[Configuring git](https://github.com/Microsoft/ostc-docs/blob/master/setup-git.md)
recommendations.

There will be three projects under bld-dsc:
```
dsc
omi
pal
```

### Building

```
cd dsc/build
./configure --enable-ulinux
make
```
- Packages are placed into `bld-dsc/dsc/release`.





### Code of Conduct

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).  For more
information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact
[opencode@microsoft.com](mailto:opencode@microsoft.com) with any
additional questions or comments.
