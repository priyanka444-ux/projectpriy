Ensure that your software packages are up to date on your instance by using the following command to perform a quick software update
[ec2-user ~]$ sudo yum update –y
Add the Jenkins repo using the following command:
[ec2-user ~]$ sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
Import a key file from Jenkins-CI to enable installation from the package:
[ec2-user ~]$ sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
[ec2-user ~]$ sudo yum upgrade
Install Java (Amazon Linux 2023):
[ec2-user ~]$ sudo dnf install java-17-amazon-corretto -y
Install Jenkins:
[ec2-user ~]$ sudo yum install jenkins -y
Enable the Jenkins service to start at boot:
[ec2-user ~]$ sudo systemctl enable jenkins
Start Jenkins as a service:
[ec2-user ~]$ sudo systemctl start jenkins
You can check the status of the Jenkins service using the command:
[ec2-user ~]$ sudo systemctl status jenkins
Configuring Jenkins
Jenkins is now installed and running on your EC2 instance. To configure Jenkins:
Connect to http://<your_server_public_DNS>:8080 from your browser. You will be able to access Jenkins through its management interface:
As prompted, enter the password found in /var/lib/jenkins/secrets/initialAdminPassword.

Use the following command to display this password:

[ec2-user ~]$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword

he Jenkins installation script directs you to the Customize Jenkins page. Click Install suggested plugins.

Once the installation is complete, the Create First Admin User will open. Enter your information, and then select Save and Continue.
On the left-hand side, select Manage Jenkins, and then select Manage Plugins.

Select the Available tab, and then enter Amazon EC2 plugin at the top right.

Select the checkbox next to Amazon EC2 plugin, and then select Install without restart.

