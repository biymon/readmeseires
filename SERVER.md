# Server Running Instructions
## Clone the repository
```
git clone git@solar-10.wpi.edu:biymon/WebServiceExpress.git
```

## Installing all related packages
```
cd WebServiceExpress
npm install
```

## Setting up `dist` folder
```
npm run-script build
```
This compiles ES6 JS code from the `src` folder to ES5 JS code into the `dist` folder that can bbe run by `node`.

## Running the PM2 server
```
cd dist/
pm2 run server.js --watch
```
The `--watch` command line argument can be removed if you don't want `pm2` to pick up file changes.

You might have to run the above command as `root` because some of the API endpoints in `server.js` write to regions on the FS with not enough permissions. Here is how you can do it:
```
sudo su -
cd /var/www/html/v4/WebServiceExpress/dist
pm2 run server.js --watch
```

## Restart the server
If you ran the server as `root`, you may have to switch to `root` with:
```
sudo su -
```

To know if the server is running as `root` or your user, run:
```
pm2 list
```
If you see a server, you are running the server as the logged in account.

To stop a server:
```
pm2 stop <id>
pm2 delete <id>
```

You can follow the steps above to start the server back up.
