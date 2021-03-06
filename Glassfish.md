# Glassfish

### Step 1: Install jdk 11 on your system

```bash
sudo apt update
sudo apt install openjdk-11-jdk
```

### Step 2: Install eclipse and Glassfish

### 2.1 Install eclipse by downloading the tar file ([https://www.eclipse.org/downloads/](https://www.eclipse.org/downloads/)) and install using the installation script name "eclipse-inst"

We will use this for creating the sample project.

### 2.2 Install Glassfish application server

Download it from ([`https://download.eclipse.org/ee4j/glassfish/glassfish-6.2.2.zip`](https://download.eclipse.org/ee4j/glassfish/glassfish-6.2.2.zip)).

You have any installation scripts for glassfish you simply extract it into your folder of choice and start using it.

```bash
	unzip glassfish-6.2.2.zip
  cd glassfish6
```

### Step 3: Change the port to `8088`

Make sure the PATH variable is set to include your glassfish server bin directory before issuing the command below

```bash
$PATH=$PATH:/Downloads/glassfish6/bin
```

Change the port using the following command:

### Note: The port for http listener is set to 8088. The admin panel still listens on 4848.

```bash

asadmin set configs.config.server-config.network-config.network-listeners.network-listener.http-listener-1.port=8088
```

 

(or optionally  goto `glasssfish6\glassfish\domains\domain1\config` folder and here open `domain.xml` file and change the port inside the `<network-listeners>` tag.

### Step 4: Start the service using:

```bash
asadmin start-domain
```

### Step 5 : Export the project you are working on as a war file from the eclipse IDE

The IDE uses the maven-war-plugin  which in turn uses `mvn` for generating the war file.The plugin was specified in the `pom.xml` file.

### Step 6: Deploy the war file using the following commands:

```bash
asadmin deploy glassfishdemo.war
```

### Relevant Screenshots/Outputs:

Application Accessible through port 8088:

![Untitled](images/Untitled.png)

Proof that application war has been deployed

![Untitled](images/Untitled%201.png)

War generation using Eclipse

 

![Untitled](images/Untitled%202.png)

![Untitled](images/Untitled%203.png)

### Bonus: Undeploying the war

Since I encountered an error in the jsp file. I had to undeploy and redeploy the new war.

You can undeploy using:

```bash
asadmin undeploy glassfishdemo
```

(Yes you have to omit the `.war`)
