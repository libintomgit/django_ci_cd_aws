# django_ci_cd_aws
Deploying Django application on aws instance using ci/cd pipeline


# Step 1 — Installing Jenkins
-First, add the repository key to your system:
```sh
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key |sudo gpg --dearmor -o /usr/share/keyrings/jenkins.gpg
```
-Next, let’s append the Debian package repository address to the server’s sources.list:
```sh
sudo sh -c 'echo deb [signed-by=/usr/share/keyrings/jenkins.gpg] http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```

- After both commands have been entered, run apt update so that apt will use the new repository.
```sh
sudo apt update
```
- Finally, install Jenkins and its dependencies:
```sh
sudo apt install jenkins
```

# Step 2 — Starting Jenkins
- now that Jenkins is installed, start it by using systemctl:
```sh
sudo systemctl start jenkins.service
```
- Chech the status
```sh
sudo systemctl status jenkins

### output should be
Output
● jenkins.service - Jenkins Continuous Integration Server
     Loaded: loaded (/lib/systemd/system/jenkins.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2022-04-18 16:07:28 UTC; 2min 3s ago
   Main PID: 88180 (java)
      Tasks: 42 (limit: 4665)
     Memory: 1.1G
        CPU: 46.997s
     CGroup: /system.slice/jenkins.service
             └─88180 /usr/bin/java -Djava.awt.headless=true -jar /usr/share/java/jenkins.war --webroot=/var/cache/jenkins/war --httpPort=8080
```

# Step 3 — Opening the Firewall
-  UFW firewall
```sh
sudo ufw allow 8080
```
- Allow open ssh and enable the frewall
```sh
sudo ufw allow OpenSSH
sudo ufw enable
```
- Check the status of the firewall
```sh
sudo ufw status
```
# Step 4 — Setting Up Jenkins

