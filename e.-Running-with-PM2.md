PM2 is a daemon process manager that will help you manage and keep your application online 24/7 (https://pm2.keymetrics.io/).

# Installing PM2

PM2 needs to be installed globally on your system.

```
npm install -g pm2
```

If you're on a VPS and the above command doesn't work, then you probably don't have the permission required to install it globally. Run it with sudo instead

```
sudo npm install -g pm2
```

PM2 needs to run all the time, this command will make PM2 start when your system boots

```
pm2 startup
```

# Ecosystem file

PM2 has a way to start a script from a file, there is a [template](https://github.com/idinium96/tf2autobot/blob/master/template.ecosystem.json) that shows what this file should look like. The file contains settings for how PM2 should run the process and the environment files that the script will run with.

Create a new file and call it `ecosystem.json` and paste in the template. If you are running the bot on a Linux VPS, then you can set `shutdown_with_message` to `false`.

# Environment variables

Configure the bot with the environment variables inside the ecosystem file, see the [configuration guide](https://github.com/idinium96/tf2autobot/wiki/b.-Configuration#environment-variables) for information on the environment variables.

# Starting the bot

Delete the `.env` file if you have made one, the ecosystem file will contain the environment variables from now on.

Navigate to the bot folder

```
cd <path to bot folder>
```

and use the command

```
pm2 start ecosystem.json
```

If you have started the bot using the ecosystem file before, then you can simply use the name of the process instead.

```
pm2 start tf2autobot
```

Once you have started the bot for the first time, you should then save the process using the command

```
pm2 save
```

This will save the process so that when you restart the processes will be saved if you have enabled startup, they will also start on startup (does not work on Windows).

# Stopping the bot

Use the command

```
pm2 stop tf2autobot
```

or navigate to the bot folder and use the command

```
pm2 stop ecosystem.json
```

# Updating environment variables

If you change the environment variables you need to use the following command to update them. Remember to be inside the bot folder because that is where the ecosystem file is located.

PM2 is a bit buggy when it comes to updating environment variables, they say that this will work but that is not always the case:

```
pm2 restart ecosystem.json --update-env
```

If it doesn't work, then try:

```
pm2 restart ecosystem.json --update-env --env production
```

or

```
pm2 restart ecosystem.json --only tf2autobot
```

This will update the environment variables and restart the bot.