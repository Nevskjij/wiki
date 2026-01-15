You will be running your bot using `pm2`. It is a daemon process manager that will help you manage and keep your application online 24/7. 
You can learn more about it [here.](https://pm2.keymetrics.io/)

# Installing PM2
PM2 needs to be globally installed on your system, to do that type and run these commands:
```
sudo npm install -g pm2
```

You will also want to have your PM2 boot-up whenever you restart your server (assuming you've followed the instructions on the initial setup of your new VPS [here](https://github.com/TF2-Price-DB/tf2autobot-pricedb/wiki/Getting-a-VPS#initial-setup-of-your-vps)).
```
sudo env PATH=$PATH:/usr/bin PM2_HOME=/home/ubuntu/.pm2 pm2 startup ubuntu -u ubuntu
sudo chown ubuntu:ubuntu -R /home/ubuntu/
```

Or if your username is not `ubuntu`, replace `<username>` to whatever your username is:
```
sudo env PATH=$PATH:/usr/bin PM2_HOME=/home/<username>/.pm2 pm2 startup ubuntu -u <username>
sudo chown <username>:<username> -R /home/<username>/
```

# Starting up the bot for the first time
- Navigate to the `tf2autobot` folder
```
cd <path of your tf2autobot folder> // Example: cd tf2autobot
```

- Start the bot with pm2, load your current environment file, and save the changes you made
```
pm2 start ecosystem.json && pm2 save
```

# Restarting the bot when you make changes to your ecosystem.json
To restart your bot after you changed your environment file you will have to tell pm2 to update its environment variables
Make sure you are inside your `tf2autobot` folder and type
```
pm2 restart ecosystem.json --update-env && pm2 save
```

# Collection of all useful pm2 commands

## Global commands
- `pm2 kill` - forced stop
- `pm2 log [processName or processId]` - to see bot’s logs
- `pm2 monit` - interactive monitor
- `pm2 list` - list of pm2 processes
- `pm2 restart <processName or processId>` - restart selected processName or processId
- `pm2 restart all` - restart all processes
- `pm2 stop <processName or processId>` - stop selected processName or processId
- `pm2 stop all` - stop all processes
- `pm2 reset <processName or processId>` - reset stats (such as restart count) of the selected processName or processId
- `pm2 reset all` - reset stats for all processes

## Updating `ecosystem.json` file
- `pm2 restart ecosystem.json --update-env` - Restart the bot and apply changes for all apps
- `pm2 restart ecosystem.json --only <processName>` - ONLY restart and apply changes on selected app 

No matter if you are running one or multiple bots, it is recommended to do `pm2 restart ecosystem.json --update-env && pm2 save && pm2 logs` to see if there are any problems after you change something in your environment file.

The next thing you should do is set up your pricelist so that your bot can start trading items. Learn how to do it [here.](https://github.com/TF2-Price-DB/tf2autobot-pricedb/wiki/What-is-the-pricelist)