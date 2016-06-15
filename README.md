Ansible role for OracleJDK installation
=======================================

Installs OracleJDK from WebUpd8 team's PPA (http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html).

Role Variables
--------------

* `oraclejdk_java_ver`

  Version of Java to install (default is `8`)

* `oraclejdk_package`

  Name of package to install (default is `oracle-java8-installer`).

* `oraclejdk_jce_package`

  Name of Java Cryptographic Extension package to install (default is `oracle-java8-unlimited-jce-policy`

* `oraclejdk_set_as_default`

  Setting JDK as default JDK. When this parameter is set to `true` then alternatvies will be updated
  and environment variables like `JAVA_HOME` will be changed. In reality it just installs
  appropriate `oracle-javaX-set-default` package. (Default is `true`).

* `oraclejdk_install_jce`

  Option to install or not install the Java Cryptographic Extension package. (Default is `true`)

* `oraclejdk_set_urandom`

  Option to set urandom as your random generator to avoid JVM delays. (Default is `true`)

Actions role
------------

* adds `webupd8team/java` PPA
* updates `apt`'s cache
* accepts Oracle's license
* installs package(s)

How to install
--------------

    ansible-galaxy install cybera.oraclejdk

For more installation's options/variants read the documentation: http://docs.ansible.com/galaxy.html

Example Playbook
----------------

Example of usage with default parameters:

    - hosts: all
      roles:
         - cybera.oraclejdk

Example of usage to install OracleJDK 7:

    - hosts: all
      roles:
         - { role: cybera.oraclejdk, oraclejdk_package: 'oracle-java7-installer' }

Example of usage to install OracleJDK 9 without Java Cryptographic Extension:

    - hosts: all
      roles:
         - { role: cybera.oraclejdk, oraclejdk_java_ver: 9, oraclejdk_install_jce: false}

License
-------

GPLv2

Author Information
------------------

Slava Semushin (slava.semushin@gmail.com)

JCE Additions by Andrew Klaus (andrewklaus@gmail.com)
