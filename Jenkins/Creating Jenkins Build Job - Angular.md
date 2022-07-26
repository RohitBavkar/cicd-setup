## **Step 1 - Install Dependencies**

### **1. Install git on Jenkins server**

```bash
sudo yum install git
```

### **2. Install NodeJS on Jenkins server**

```bash
sudo dnf module list nodejs
```

```bash
sudo dnf module install nodejs:16
```

## **Step 2 - Install Dependencies**

### **Install Angular on Jenkins serve**

```bash
sudo npm install -g @angular/cli
```

## **Problems**

### **1. Can not store the git token in public repo**

1. If we store the git token in public repo then GitHub automatically deletes the token.
2. So saved encrypted token in .txt file using

    ```bash
    echo "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" | openssl enc -aes-256-cbc -md sha512 -a -pbkdf2 -iter 100000 -salt -pass pass:Secret@123# > git-token.txt
    ```

3. Decrypted using

    ```bash
    cat git-token.txt | openssl enc -aes-256-cbc -md sha512 -a -d -pbkdf2 -iter 100000 -salt -pass pass:Secret@123#
    ```


### **2. jar command not found**

```bash
yum install java-devel
```

### **3. "ng b" command was killed automatically**

It was RAM issue, as 1 GiB RAM was not enough. To solve we can add swap memory, or get a better server.(Upgraded from t2.micro to t4g.small)