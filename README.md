Installing Jenkins directly in VM:

Installing jdk:
https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
https://docs.oracle.com/javase/8/docs/technotes/guides/install/linux_jdk.html
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
