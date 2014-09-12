services-checker
================

Bash Script to check if services are running and restart if not. Sends email to you.


#INSTALL:

1. put into your scripts folder
2. set your email address
3. set the services you want to keep an eye on (by default it has mysql and apache2..you can add or take away whatever you need)
3. save your changes
4. create a cronjob as root (sudo crontab -e)  and add something like this, which runs every minute (adjust to your needs):



```
#check on services
*/1 *  * * * /your/path/to/scripts/services

```

The script will look at the exit code after checking the status of each service. If the service is stopped (exit code 3), it tries to restart the service. If the service status then gives an exit code of 0, it sends you an email saying the service stopped, but was restarted.

If the service does not start for some reason, it sends you an email telling you it was not started.


#################################################
#WISH LIST:

- rather than sending new emails for a service that won't restart, it would be cool if it could try maybe 3 times and then give up. Not sure how to do that yet.






