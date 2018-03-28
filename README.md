# PM2 command lines:
## Start an application:
```
pm2 start your_app.js
```
PM2 can automatically restart your application when a file is modified in the current directory or its subdirectories:
```
pm2 start your_app.js --watch
```
## Restart an application 
```
pm2 restart your_app.js
```

## Stop an application 
```
pm2 stop your_app.js
```



# PM2 Quick Start

[http://pm2.keymetrics.io/docs/usage/quick-start/](http://pm2.keymetrics.io/docs/usage/quick-start/)


# Steps of running nodejs application on Apache2  
If you want to run a new nodejs application
1. get the latest code at /var/www/html/rest/your_application_folder
2. run your application with pm2
```
pm2 start your_app.js --watch
```
If you can see an application named your_app with a green 'online' word in 'status' column, it means your application run successfully.

3. go to /etc/apache2/sites-available
4. open beesite.conf
   add the following lines after </Proxy>
  ```
	ProxyPass /user_defined_path http://localhost:user_defined_port(your nodejs application used)
	ProxyPassReverse /user_defined_path http://localhost:user_defined_port/user_defined_path
  ```
5. save beesite.conf and test if the beesite.conf contains grammar and setting errors
  ```
  sudo apache2ctl configtest
  ```
6. If there is no error happened in step 5, restart apache2.
```
sudo service apache2 restart"
```

Try "http://beecology.wpi.edu/user_defined_path" to see if it is accessible.http://pm2.keymetrics.io/docs/usage/quick-start/
