# jenkinsinstallation

---

# Jenkins Installation Guide

This guide provides step-by-step instructions for installing Jenkins on an Ubuntu t2.micro instance with 8GB of RAM.

## Prerequisites

1. An AWS t2.micro instance running Ubuntu.
2. Ensure that you have allowed inbound traffic for:
   - SSH (Port 22) from your IP address.
   - Custom TCP (Port 8080) from your IP address.
   
## Installation Steps

### Step 1: Update and Install OpenJDK
1 
```bash
apt search jdk
```
2 
```bash
add-apt-repository ppa:openjdk-r/ppa
```

3. Install the latest version of OpenJDK (Java Development Kit):

   ```bash
   sudo apt install openjdk-11-jdk
   ```

### Step 2: Install Jenkins

1. Add the Jenkins repository and its GPG key:

   ```bash
   curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
   echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
   ```

2. Update the package list again:

   ```bash
   sudo apt-get update
   ```

3. Install Jenkins:

   ```bash
   sudo apt-get install jenkins
   ```

### Step 3: Start Jenkins and Get Initial Admin Password

1. Check the status of the Jenkins service:

   ```bash
   systemctl status jenkins
   ```
 use public address of ec2 instance with:8080
2. Retrieve the initial admin password:

   ```bash
   cat /var/lib/jenkins/secrets/initialAdminPassword
   ```

3. Copy the generated password; you will need it to unlock Jenkins.

### Step 4: Access Jenkins Web Interface

1. Open a web browser and go to the following URL, replacing `<instance-ip>` with your instance's public IP address and `8080` with the custom TCP port:

   ```
   http://<instance-ip>:8080/
   ```

2. Paste the initial admin password that you copied earlier.

3. Follow the on-screen instructions to complete the Jenkins setup.

## Jenkins Access

Once Jenkins is set up, you can access it at:

```
http://<instance-ip>:8080/
```

