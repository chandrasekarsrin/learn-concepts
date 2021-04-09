# Fedora
- a type of linux distribution


## Package Managers:
### rpm
- helps to install, update and remove software packages.
- helps to deploy indvidual packages but gets difficult if we want to manage lot of packages. yum comes to rescue there.

rpm -q java
package java is not installed.

### yum
- allows to deploy collection of packages by installing repositories.
- 

yum update -y
- tells to update all the packages on the system

yum install -y java-11-openjdk
yum list all | grep java
#### Option 1: 
cd /etc/yum.repos.d
vi public-yum-ol7.yum
edit the public repos

#### Option 2:
1. download the repo
1. install with rpm -Uvh
1. and yum list all
1. install required package in this new repository.

### Installing manually
# Install Git
RUN set -ex \
   && GIT_VERSION=2.27.0 \
   && GIT_TAR_FILE=git-$GIT_VERSION.tar.gz \
   && GIT_SRC=https://github.com/git/git/archive/v${GIT_VERSION}.tar.gz  \
   && curl -L -o $GIT_TAR_FILE $GIT_SRC \
   && tar zxvf $GIT_TAR_FILE \
   && cd git-$GIT_VERSION \
   && make -j4 prefix=/usr \
   && make install prefix=/usr \
   && cd .. ; rm -rf git-$GIT_VERSION \
   && rm -rf $GIT_TAR_FILE /tmp/*

