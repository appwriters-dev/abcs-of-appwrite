---
id: ls03-production-tips
title: Configuring Appwrite for Production
---

Appwrite already comes with a sane default during installation. However, running in production, you want to personalize Appwrite for your particular needs, as well as make further adjustments for performance and stability. In this section we will look at what environment configurations we might want to change for production use case.

Before you begin installation in your production server, make sure you have a domain assigned that you will use to access Appwrite’s API and admin console. Doing this ensures Appwrite will generate SSL certificates for the assigned domain and configurations are set properly during the installation. However, you can always modify the environment variables later to provide these values as we saw in the above section. Once you have assigned domain and you are logged in to your production server where you want to install the Appwrite, you can run the same installation command.

During the installation, assign your domain when asked for the host name. Also make sure you provide a secure, long, random secret key for encryption (keep a backup copy of your encryption key, because if you loose it, all the encrypted data will be lost).

If you want to change the encryption key later update `_APP_OPENSSL_KEY_V1` value.

```
_APP_OPENSSL_KEY_V1=<your-new-secret-key>
```

> Warning! Changing the encryption key, will invalidate any data that was already encrypted. So make sure you have backed-up all your data before you change it

To change the primary domain, you can update `_APP_DOMAIN` and `_APP_DOMAIN_TARGET`. They both are usually same. The `_APP_DOMAIN_TARGET` is required if you plan to add more custom domains into Appwrite, issue certificates for those and make secured request from those domains to your Appwrite project.

```
_APP_DOMAIN=<your-production-domain>
_APP_DOMAIN_TARGET=<your-production-domain>
```

Now that you have proper domain and encryption key setup, we can move on to other settings that we can change.

1. `_APP_ENV` This will usually be the first environment variable available in your `.env` file if you have just installed Appwrite. This can have one of two values `production` or `development`. By default this should already be set to `production`. However if set to `development` you get more detailed error messages with stack traces when error occurs. So if you are running your Appwrite instance in production, with public access, make sure to set this variable to `production`.
2. `_APP_OPTIONS_FORCE_HTTPS` This environment variable allows to force HTTPS connection to the server. In production, when you assign a proper domain to Appwrite installation, Appwrite automatically generates a SSL certificate, so it’s is advised to set this to `enabled` when running in production, so that your application always connect using secure HTTPS channel.
3. `_APP_OPTIONS_ABUSE` This environment variable is used to enable abuse protection. This should be `enabled` by default. If not you should set it to `enabled` and this will prevent any user from trying to abuse your Appwrite instance.
4. `_APP_STORAGE_LIMIT` This environment variable tells the largest file size that user can upload to Appwrite storage. This is in bytes. By default it’s set to `30000000` (i.e. 30MB). You can set it to the size required by the applications being served your Appwrite instance. However, this can also be configured in each bucket so setting this to max you want to allow and configuring the least required for each bucket is advised. We will talk about Storage service and buckets in a different book.
5. `_APP_STORAGE_PREVIEW_LIMIT` This is the largest image size that will be allowed by the storage preview endpoint to create a customized preview set in bytes. Setting this too high requires your system to have more memory and CPU as to manipulate large image file, system requires more resources. I recommend to set this only as high as required. If for example you allow people to upload at most 5MB image in your application then you can set this to `5000000` i.e. 5MB.

### Email Setup

In a production Appwrite instance it is advised to setup email providers. Doing this you will be able to use various functionalities of Appwrite accounts service.

1. You as console admin can use password reset service in console if you ever forgot your admin password.
2. Your applications can use features like email verification, password reset and magic link authentication

To setup email service for production, first you need to update the following system environment.

1. `_APP_SYSTEM_EMAIL_ADDRESS` This will be used as the from email address while sending emails from your Appwrite instance/project. You should choose an email address that is allowed to be used from your SMTP provider to avoid the email ending in the users' SPAM folders.
2. `_APP_SYSTEM_EMAIL_NAME` This is the name that will appear on email messages sent Appwrite console. The default value is: `Appwrite`. Replace it with name suitable to your project/company. You should use url encoded strings for spaces and special chars.

Next, you need to setup the SMTP related environment variables to setup email service provider.

1. `_APP_SMTP_HOST` SMTP server host name address, this will be provided by your email service provider like mailgun, sendgrid. To disable email service you can leave this as the default value which is an empty string
2. `_APP_SMTP_PORT` SMTP server TCP port. This again will be provided by the service provider. Default value is empty
3. `_APP_SMTP_SECURE` The secure protocol to be used by the email service provider. Default means the provider doesn’t provider a secure connection. If it does, change the value to `tls`.
4. `_APP_SMTP_USERNAME` & `_APP_SMTP_PASSWORD` Username and password required by your email service provider to authenticate.

More details regarding the environment variables associated with email server can be found at the official environment documentation at [https://appwrite.io/docs/environment-variables#smtp](https://appwrite.io/docs/environment-variables#smtp).

By now you know how to setup basic server configurations and also know how to setup email service. Next up, if you want to use phone based authentication in your mobile application, you also need to setup providers for phone authentication.

1. `_APP_PHONE_PROVIDER` SMS service provider to be used for phone authentication. You need to provide the value in the following format. `phone://[USER]:[SECRET]@[PROVIDER]. The providers supported as of now are `twilio`, `text-magic` and`telesign`.
2. `_APP_PHONE_FROM` Phone number used when sending out messages. Must start with a leading `+` sign and maximum of 15 digits without spaces. This should be the phone number allowed by your phone provider as a sender number.

### Giving Access to Other Team Members

Appwrite’s console provides unrestricted access to Appwrite and it’s resources. In production Appwrite instance, it is crucial as to who can have access to console. There are couple of environment variables you can use to configure access to the console.

1. `_APP_CONSOLE_WHITELIST_ROOT` Enabled by default, this option allows only one user to be able to use the registration form to signup for the console. New users can only be added by inviting them to the project by the root user. If you are the only one using the server its safe to set this as enabled.
2. `_APP_CONSOLE_WHITELIST_EMAILS` Another option, most suitable for organizations or small teams is to whitelist the emails that can signup to create new account on the console. In order to enable this pass a comma separated list of emails in this variable. For example setting `_APP_CONSOLE_WHITELIST_EMAILS=user1@organization.com,user2@organization.com` will allow only those emails to sign up to create account in the console. Make sure to set `_APP_CONSOLE_WHITELIST_ROOT=disabled` to use the whitelisted emails.
3. `_APP_CONSOLE_WHITELIST_IPS` Finally one more option to limit creation of users in console only for the user sharing the same set of IP addresses. This is suitable for a team working with a VPN service or a company IP. To enable this you can pass a comma separated list of allowed IP addresses.

<!--- ### Setting up Loggers

1. Logging Provider to receive important system logs

// hosted database - change the database username, password and root password if using the local instance

// hosted redis?

// external storage (S3 or DO Spaces or Other )

## Tips Upgrading Appwrite

### May Be?

- Running Multiple Instances of Appwrite in Same Machine ??
- One click DO setup?
-->