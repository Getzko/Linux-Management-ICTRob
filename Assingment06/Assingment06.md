# Part 1: Understanding APT & Systems Updates
 1. APT Version
```bash
azureuser@round3:~$ apt --version
apt 2.8.3 (amd64)
```
 2. sudo apt update is important to keep your files always up to date, since the previous versions or those already pre-installed on your virtual machine might be faulty / missing important features.
 3. The difference between update and upgrade is that update refreshes all avaible packages and their repository versions. The upgrade does the installation.
 4. After the upgrade and update, nothing appears on the list.
# Part 2: Installing & Managing Packages
 1. The image editor I found ( and remember using long time ago)
```bash
gimp/noble-updates 2.10.36-3ubuntu0.24.04.1 amd64
  GNU Image Manipulation Program
```
 2. It requires alot of dependecies with lib- prefixes. E.g. libgimp2, libbabl and libheif1. All dependencies have a version number that should be higher than shown to ensure correct workflow of the application. 
 3. Now I install gimp to my vm. The package is successfully installed after the program baisically shows that the servicies are restarted and there are no problems.
 4. The 2.10.36 version was installed
```bash
gimp-data/noble-updates,now 2.10.36-3ubuntu0.24.04.1 all [installed,automatic]
gimp/noble-updates,now 2.10.36-3ubuntu0.24.04.1 amd64 [installed]
libgimp2.0t64/noble-updates,now 2.10.36-3ubuntu0.24.04.1 amd64 [installed,automatic]
```
# Part 3: Removing & Cleaning Packages
 1. Gimp is now successfully removed
 ```bash
 0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 20.0 MB disk space will be freed.
(Reading database ... 124869 files and directories currently installed.)
Removing gimp (2.10.36-3ubuntu0.24.04.1) ...
Processing triggers for man-db (2.12.0-4build2) ...
```
 2. Purge removes everything, remove leaves configuration files. Since there were no config files, nothing was 'purged'
 3. The autoremove deletes packages that were installed as dependencies of other packages and linux does not need them anymore. It's important to keep your disc clean.
 4. sudo apt clean deletes .deb files from local cashe. After installing a package, they are irrelevant.
# Part 4: Managing Repositories & Troubleshooting
 1. This is config file for APT. It tells the system from where to download the packages from. It contains URI, categories of packages and keys.
Main - ubuntu supported packages
universe - community ones
restricted - packages only accesible with a key
2. 
```bash
Hit:1 http://azure.archive.ubuntu.com/ubuntu noble InRelease
Hit:2 http://azure.archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:3 http://azure.archive.ubuntu.com/ubuntu noble-backports InRelease
Hit:4 http://azure.archive.ubuntu.com/ubuntu noble-security InRelease
```
3. An error appears - unable to locate package (packagename). To troubleshoot this issue I would double check the correct spelling of the package, or if its in a different repo then add that repo to my source.
4. Probably if we had to 'hold' a package from being updated, it's probably because a program or code that barely works with it ( a program maybe in it's alpha stage) and we want to ensure no update ruins our program. That is my guess.
```bash
azureuser@round3:~$ sudo apt-mark hold gimp
gimp set on hold.
```