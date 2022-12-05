---
id: ls01-installing-locally-or-in-cloud
title: Installing Locally or in Cloud
---

Installing and running Appwrite is as easy as running one command. Appwrite can be installed and run on any system that supports Docker either it’s local or in the cloud. So make sure you have [Docker](https://docker.com) installed in the system you are trying to install Appwrite. Docker is a free tool, which you can download and install from [https://www.docker.com/get-started](https://www.docker.com/get-started/). You can make sure that the docker and docker compose is installed correctly by running the following command in your terminal.

```bash
docker --version
# Output should be similar to: Docker version 20.10.12, build e91ed57

docker compose version
# Output should be similar to: Docker Compose version v2.2.3
```

> **Did you know**: Appwrite can run on Raspberry Pi as well, how cool is that?

### System Requirement

Before you install Appwrite, you should know that your system supports Appwrite. In order to properly run Appwrite you need at least **1 CPU** core and **2 GB** free memory.

### Installation

Installing and running Appwrite is very simple as, all you need to do is run a single docker command from your terminal. Make sure you are in a directory where you want to install Appwrite and run one of the following command based on your operating system.

**Linux / MacOS**

```bash
docker run -it --rm \
    --volume /var/run/docker.sock:/var/run/docker.sock \
    --volume "$(pwd)"/appwrite:/usr/src/code/appwrite:rw \
    --entrypoint="install" \
    appwrite/appwrite:1.0.0
```

**Windows**

CMD

```bash
docker run -it --rm ^
    --volume //var/run/docker.sock:/var/run/docker.sock ^
    --volume "%cd%"/appwrite:/usr/src/code/appwrite:rw ^
    --entrypoint="install" ^
    appwrite/appwrite:1.0.0
```

PowerShell

```powershell
docker run -it --rm ,
    --volume /var/run/docker.sock:/var/run/docker.sock ,
    --volume ${pwd}/appwrite:/usr/src/code/appwrite:rw ,
    --entrypoint="install" ,
    appwrite/appwrite:1.0.0
```

The above command will pull the Appwrite docker image and then install and run Appwrite version 1.0.0. You usually just need to change `1.0.0` to the desired latest version of Appwrite in order to install that particular version. You can get the latest command to install latest available version from the official installation docs at [https://appwrite.io/docs/installation](https://appwrite.io/docs/installation).

After you run the above installation command, it will ask you a series of questions.

```jsx
Starting Appwrite installation...
Choose your server HTTP port: (default: 80)

Choose your server HTTPS port: (default: 443)

Choose a secret API key, make sure to make a backup of your key in a secure location (default: 'your-secret-key')

Enter your Appwrite hostname (default: 'localhost')

Enter a DNS A record hostname to serve as a CNAME for your custom domains.
You can use the same value as used for the Appwrite hostname. (default: 'localhost')
```

Well, if you are installing for development, you can leave all these as default value. However if you wish you can change the default ports, host name and also the encryption key. After providing answer to all these questions, the Appwrite should create the configurations needed for it to run and start the application. You should see an information similar to the following in the terminal.

```jsx
Running "docker compose -f /usr/src/code/appwrite/docker-compose.yml up -d --remove-orphans --renew-anon-volumes"
Appwrite installed successfully
```

Inside the working directory where you ran the command, the installation script will create a a folder named `appwrite` inside which there will be two files. The `docker-compose.yml` file contains the docker configuration to run all the micro service containers required by Appwrite to work properly and `.env` file contains all the environment configuration required for Appwrite. To run Appwrite locally for development purpose, you don’t need to make any changes to the environment configuration.

Once Appwrite is installed, you should be able to access the admin console via the host name and port you provided during installation `http://<host-name>:<port>` or using `https` and the HTTPS port you provided. if you used all the default options, you should be able to access it in [http://localhost](http://localhost). However make sure you use the correct port and domain you provided during installation.
