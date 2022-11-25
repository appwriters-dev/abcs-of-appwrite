---
id: ls02-checking-health
title: Checking Appwrite System Health
---

Once Appwrite is installed, you can also check the health of the overall system to make sure it’s running in full capacity and proper configurations. To do so you can use the `doctor` CLI command provided by Appwrite. Run the following command from the installation folder.

```jsx
docker compose exec appwrite doctor
```

It should show the output similar to the following

```jsx
  __   ____  ____  _  _  ____  __  ____  ____     __  __  
 / _\ (  _ \(  _ \/ )( \(  _ \(  )(_  _)(  __)   (  )/  \ 
/    \ ) __/ ) __/\ /\ / )   / )(   )(   ) _)  _  )((  O )
\_/\_/(__)  (__)  (_/\_)(__\_)(__) (__) (____)(_)(__)\__/ 

👩‍⚕️ Running Appwrite Doctor for version 1.0.0 ...

Checking for production best practices...
🔴 Hostname has no public suffix (localhost)
🔴 CNAME target has no public suffix (localhost)
🔴 Not using a unique secret key for encryption
🟢 App environment is set for production
🟢 Abuse protection is enabled
🟢 Console access limits are enabled
🔴 HTTPS force option is disabled
🔴 Logging adapter is disabled

Checking connectivity...
Database............connected 👍
Queue...............connected 👍
Cache...............connected 👍
SMTP.............disconnected 👎
StatsD..............connected 👍
InfluxDB............connected 👍

Checking volumes...
🟢 Uploads Volume is readable
🟢 Uploads Volume is writeable
🟢 Cache Volume is readable
🟢 Cache Volume is writeable
🟢 Config Volume is readable
🟢 Config Volume is writeable
🟢 Certs Volume is readable
🟢 Certs Volume is writeable

Checking disk space usage...
🟢 Uploads Volume has 29.26GB free space (9.18% used)
🟢 Cache Volume has 29.26GB free space (9.18% used)
🟢 Config Volume has 29.26GB free space (9.18% used)
🟢 Certs Volume has 29.26GB free space (9.18% used)
```

Anything in red means, things you should change or configure to make it more robust. However if you are in development mode, running locally, it’s fine to not have valid host name or not having unique secret key for encryption and all. We will see in later section how we can update some of the settings to solve the issues reported here by the doctor for running in production.

Now that we know what Appwrite is and how to install and get it running, in the next section let’s learn about Appwrite environment variables and how we can use those to customize our Appwrite installation.

## Understanding Appwrite Environment Configuration

Appwrite provides lots of configuration options to customize your Appwrite installation. There are tons of Appwrite environment variables that you can change to customize Appwrite. We will talk about how to change the environment configuration of your Appwrite installation in this section. To find the most up to date and all environment variable information, please visit the official documentation at [https://appwrite.io/docs/environment-variables](https://appwrite.io/docs/environment-variables).

Appwrite environment variables are divided into categories. First lets talk about the, general environment variables that are not related to specific features or service.

As we talked in the previous section, when you install Appwrite in the installation directory there’s a `.env` file. Appwrite already comes with a sane default to run Appwrite in development mode. So when you open the `.env` file in text editor you can see many environment variables with default values already assigned. So how can we change them?

First open `.env` file in your favorite text editor. You can see various environment variables and their default values. In the file find `_APP_CONSOLE_WHITELIST_ROOT`, by default this should be set to `enabled`. Right now if you have signed up after installation in the previous section, if you try to signup again with another email address it will fail. As this environment variable tells Appwrite to allow only one signup to the console. However, we can change that and allow anyone to sign up. **Caution, not recommended in production.** Change the value from `enabled` to `disabled`. Once we change the environment variable, we need to let docker know that the environment variables have changed. To do that we need to run the following command. In the terminal navigate to the folder where you have your Appwrite installation (folder containing your `.env` and `docker-compose.yml` file) and run the following command.

```jsx
docker compose up -d
```

This tells docker to look for configuration change and restart if there’s any change. So docker will know that our `.env` has changed, so it will restart all the relevant services using the changed environment variable so that they can receive the new value.

After the above command successfully executes, if you try to signup again, you should be able to create new account in the console.

> **Dont Forget** to run the docker command whenever you change values in `.env` file, otherwise you will still be running Appwrite with old values.
> 

To make sure that Appwrite is running with the up-to date values for environment variables, you can use `env` CLI command provided by Appwrite. While still in the Appwrite installation folder with the `docker-compose.yml` file in the terminal run the following command

```jsx
docker compose exec appwrite env
```

This command should show the list of all the environment variables and their values that are being used by your Appwrite installation. If you see any difference between the value displayed here and in the value provided in the `.env` file, you should run `docker compose up -d` command again to make sure the environment changes take effect.

Now, that we know the basics of Appwrite environment configurations and how we can modify them. In the next section, we will learn what environment variables we can use to make Appwrite secure and performant while running in production.