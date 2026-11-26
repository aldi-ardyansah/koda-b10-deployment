# Deployment

## Minitask: File Permissions & Ownership Practice

## 1. Initial Setup

### Shell Command
Go to /srv folder:
```sh
cd /srv
```
Create /srv/projectX directory:
```sh
sudo mkdir projectX
```
Add user "koda":
```sh
sudo adduser koda
```
Add user "dako":
```sh
sudo adduser dako
```
Add group "devteam" and add user "koda" and "dako" to group "devteam":
```sh
sudo groupadd devteam
sudo usermod -aG devteam koda
sudo usermod -aG devteam dako
```

### Screenshoot
![1a.png](img/1a.png)
![1b.png](img/1b.png)
![1c.png](img/1c.png)

## 2. Make koda the owner and devteam the group owner of /srv/projectX

### Shell Command
```sh
sudo chown -R koda:dako /srv/projectX
sudo usermod -aG sudo koda
```

### Screenshoot
![2.png](img/2.png)

## 3. Restricting access

### Shell Command
```sh
sudo chmod 750 /srv/projectX
```

### Screenshoot
![3.png](img/3.png)

## 4. Create the following structure as user koda

### Shell Command
```sh
su koda
touch README.md
mkdir src
mkdir data
touch ./src/app.sh
touch ./data/input.txt
```

### Screenshoot
![4.png](img/4.png)

## 5. Fixing permissions

### Shell Command
```sh
chmod ug+x,o-x ./src/app.sh
```

### Screenshoot
![5.png](img/5.png)

## 6. Protecting sensitive data

### Shell Command
```sh
chmod 600 ./data/input.txt
```

### Screenshoot
![6.png](img/6.png)

## 7. Allow group collaboration

### Shell Command

 Changes the group ownership of src and all files inside it (-R) to group "devteam":

```sh
chgrp -R devteam ./src
```

 Grants the group (g) read (r) and write (w) permissions:
 ```sh
chmod -R g+rwX ./src
```

### Screenshoot
![7.png](img/7.png)

## 8. Change ownership

### Shell Command
```sh
chown -R koda:devteam /srv/projectX
```

### Screenshoot
![8.png](img/8.png)

## 9. Prevent accidental deletion

### Shell Command
```sh
chmod -R u=rwX,g=rwXs,o=rX /srv/projectX
```

### Screenshoot
![9.png](img/9.png)

## 10. Make Readme readonly

### Shell Command
```sh
sudo chmod 644 /srv/projectX/README.md
```

### Screenshoot
![10.png](img/10.png)

## 11. Resignation and project handover

### Shell Command
```sh
sudo chown -R dako:devteam /srv/projectX
```

### Screenshoot
![11.png](img/11.png)