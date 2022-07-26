## **Step 1 - Setup Creation**

---

1. Create Free tier EC2 instance with key.(key will be needed to connect server)
2. Create new or use existing Security Group with Inbound Rule for port 8080 and type is Custom TCP.

## **Step 2 - Connect to Server using putty**

---

1. Download server key(.pem) and convert it(.ppk) using puttygen with ssh option.
2. Launch putty and in auth section select the converted key
3. Hostname will be public IP address or public DNS(which changes every time when server is restarted).
4. Port Number will be 22.

## **Step 3 - Installing Dependency**

---

1. Jenkins need Java

    ```bash
    sudo dnf install java-11-openjdk/co
    ```


## **Step 4 - Installing Jenkins**

---

1. Download Jenkins Package

    ```bash
    sudo yum install wget
    ```

    ```bash
    sudo wget -O /etc/yum.repos.d/jenkins.repo [https://pkg.jenkins.io/redhat-stable/jenkins.repo](https://pkg.jenkins.io/redhat-stable/jenkins.repo)
    ```

2. Get Jenkins Key

    ```bash
    sudo rpm --import [https://pkg.jenkins.io/redhat-stable/jenkins.io.key](https://pkg.jenkins.io/redhat-stable/jenkins.io.key)
    ```

3. Upgrade your system to the current release of Fedora

    ```bash
    sudo dnf upgrade
    ```

4. Install Jenkins

    ```bash
    sudo dnf install jenkins
    ```

5. Reload the unit configuration files(notifies the system about the changes in the configurations)

    ```bash
    sudo systemctl daemon-reload
    ```


## **Step 5 - Start Jenkins**

---

1. Start the Jenkins

    ```bash
    sudo systemctl start jenkins
    ```

2. Or enable the Jenkins service to start at boot

    ```bash
    sudo systemctl enable jenkins
    ```

3. Check the status of the Jenkins service

    ```bash
    sudo systemctl status jenkins
    ```


## **Step 6 - Post-Installation Setup**

---

1. Access Jenkins
    1. Browse to -> [http://pulic-DNS:8080](http://pulic-dns:8080/)
    2. Get one time admin password and unlock Jenkins -> sudo cat /var/lib/jenkins/secrets/initialAdminPassword
2. Install Suggested Plugins
3. Create First Admin User
4. Start Using Jenkins

## **Problems**

---

1. Jenkins was not starting with Java-17

   Reason -> Java 8 or Java 11 are required for running modern versions of Jenkins.

   Solution -> Switched to Java 11.