Installing Jenkins directly in VM:

Installing jdk:
https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
https://docs.oracle.com/javase/8/docs/technotes/guides/install/linux_jdk.html

```
https://docs.oracle.com/javase/8/docs/technotes/guides/install/linux_jdk.html#BJFGGEFG
Installation of the 64-bit JDK on Linux Platforms
This procedure installs the Java Development Kit (JDK) for 64-bit Linux, using an archive binary file (.tar.gz).

These instructions use the following file:

jdk-8uversion-linux-x64.tar.gz
Download the file.

Before the file can be downloaded, you must accept the license agreement. 
The archive binary can be installed by anyone (not only root users), in any location 
that you can write to. However, only the root user can install the JDK into the system location.

Change directory to the location where you would like the JDK to be installed, 
then move the .tar.gz archive binary to the current directory.

Unpack the tarball and install the JDK.

% tar zxvf jdk-8uversion-linux-x64.tar.gz
The Java Development Kit files are installed in a directory called jdk1.8.0_version in the current directory.

Delete the .tar.gz file if you want to save disk space.
```
check if wget is present, if not install it with
```sudo yum install wget```

To download java, use below command, replace download url

Note: java8 url https://download.oracle.com/otn-pub/java/jdk/8u201-b09/42970487e3af4f5aa5bca3f542482c60/jdk-8u201-linux-x64.rpm
```
wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://link_copied_from_site"

 wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "https://download.oracle.com/otn-pub/java/jdk/8u201-b09/42970487e3af4f5aa5bca3f542482c60/jdk-8u201-linux-x64.rpm"
 
 
 $ sudo yum localinstall jdk-9.0.4_linux-x64_bin.rpm
 [mukesh@jenkins-master ~]$ java -version
java version "11.0.2" 2019-01-15 LTS
Java(TM) SE Runtime Environment 18.9 (build 11.0.2+9-LTS)
Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.2+9-LTS, mixed mode)
```

Install Tomcat
$ wget http://ftp.man.poznan.pl/apache/tomcat/tomcat-9/v9.0.14/bin/apache-tomcat-9.0.14.zip
$ unzip apache-tomcat-9.0.14.zip
create link tomcat
$ ln -s apache-tomcat-9.0.14 tomcat

Installing Jenkins:
Jenkins is available at http://mirrors.jenkins.io/war-stable/latest/jenkins.war
$ wget http://mirrors.jenkins.io/war-stable/latest/jenkins.war

Move war file to tomcat webapp

Ensure the system property org.apache.tomcat.util.buf.UDecoder.ALLOW_ENCODED_SLASH has been set to true,
You can set this property before starting Tomcat by either:
Setting $CATALINA_OPTS with the value:
-Dorg.apache.tomcat.util.buf.UDecoder.ALLOW_ENCODED_SLASH=true.
or
Adding the following to the catalina.properties file:
org.apache.tomcat.util.buf.UDecoder.ALLOW_ENCODED_SLASH=true.

To set the $JENKINS_HOME directory, do one of the following before starting Tomcat:
Setting $CATALINA_OPTS with the value:
-DJENKINS_HOME=/path/to/jenkins_home/.

Setting $JENKINS_HOME with its path value - for example:
export $JENKINS_HOME=/path/to/jenkins_home/ (before running the command to start Tomcat).
