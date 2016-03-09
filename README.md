# centos-6-php-suhosin-rpm
php suhosin was discontinued in EPEL because maintainers abandoned the project and some said they couldnt build the rpms. This repo allows users the option to still use it.


Instructions.

Use the provides spec files to compile rpms.

1. Set up your build environment per these instructions https://wiki.centos.org/HowTos/SetupRpmBuildEnvironment
2. As root run this command "yum-builddep php.spec" in the same directory as spec file provided (wherever you downloaded it to) This will install all of the required packages to build php.
3. Run rpmbuild -ba on each spec file with all source files downloaded in their proper place, sign and install the rpms as needed.
 

Note: I have removed a few patches to allow it to compile, they were either unneeded or covered by the suhosin patch itself (in the case of one security update) 


Easy mode: Install my precompiled binaries.

wget http://laurelai.info/security/repo/RPM-GPG-KEY-Laurelai

rpm --import RPM-GPG-KEY-Laurelai

wget -O /etc/yum.repos.d/centos-security.repo http://laurelai.info/security/repo/centos-security.repo

yum -y update

yum install php-suhosin
