https://jenkins.io/doc/book/installing/

sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key

Then, you can install Jenkins. The following command also ensures you have java installed.

sudo dnf upgrade && sudo dnf install jenkins java
Next, start the Jenkins service.

sudo service jenkins start
sudo chkconfig jenkins on

systemctl status jenkins
