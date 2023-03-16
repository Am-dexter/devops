# Installing Jenkins Server

## About Jenkins
Jenkins is one of the most popular open-source automation servers, often used to orchestrate continuous integration (CI) and/or continuous deployment (CD) workflows

## Installing Jenkins on Ubuntu server

The following provides a guide to install Jenkins on Ubuntu. I have created a script should you need to run it. 

1. Update the system 
    > sudo apt update

2. Add repository key to your system
    > wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key |sudo gpg --dearmor -o /usr/share/keyrings/jenkins.gpg

The gpg --dearmor command is used to convert the key into a format that apt recognizes.

3. Append the Debian package repository address to the sources.list file
    > sudo sh -c 'echo deb [signed-by=/usr/share/keyrings/jenkins.gpg] http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

4. run *apt update* so that *apt* can use the new repository
    > sudo apt update

5. Finally, install Jenkins and its dependancies
    > sudo apt install jenkins

## Starting the Jenkins Server

With Jenkins installed, we can start it with *systemctl*
    > sudo systemctl start jenkins

With Jenkins started, you can access it via browser on [IP] and port [8080]. Should you not be able to access, open the port on the firewall using *ufw*
    > sudo ufw allow 8080

Confirm new rules with
    > sudo ufw status

## Setting Up Jenkins

To set up your installation, visit Jenkins on its default port, 8080, using your server domain name or IP address: http://your_server_ip_or_domain:8080

You should receive the Unlock Jenkins screen, which displays the location of the initial password:

![Initial Jenkins Page!](/home/dexter/Downloads/unlock-jenkins.png "Jenkins Unlock")

In terminal window use [cat] to display the password

    > sudo cat /var/lib/jenkins/secrets/initialAdminPassword

Click continue and [Install suggested plugins]. When this process is complete you'll be prompted to setup the frst admin user. It's possible to skip but recommended to have a new user. 

When all is done, you'll receive a message that Jenkins is ready!! 

