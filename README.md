## Services Checker

Bash Script to check if services are running and restart if not. Sends email to you.
Tested with Ubuntu 14.04, 16.04 and 18.04.

## Installation

1. Put it into your scripts folder
2. Uncomment the email and set your email address if you want an email notification
3. Uncomment the log option if you want a log-file (it creates it automatically in the same directory as the script)
4. Set the services you want to keep an eye on (by default it has `mariadb` and `apache2`... you can modify them as you need)  For ubuntu 20.04 and below I had to use mysql instead of mariadb. In ubuntu 22.04 I had to use mariadb
5. Save your changes
6. Ensure it has enough privilege to run:

```
chmod +x /your/path/to/scripts/restart-services
```

6. Create a cronjob as root (sudo crontab -e)  and add something like this, which runs every minute (adjust to your needs):



```
#check on services
*/1 *  * * * /your/path/to/scripts/restart-services

```

The script will check the status of each service. If the service is stopped, it tries to restart the service. If the service starts, it sends you an email saying the service stopped but was restarted.

If the service does not start for some reason, it sends you an email telling you it was not started.

After that, it will continue to try and start, but not send any more emails until the service is finally started.
