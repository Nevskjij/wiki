This page will go through how to set up the bot on a Linux server so that it will run 24/7.

# Getting a VPS

You can get a VPS from many different providers, but I recommend getting one from DigitalOcean. If you haven't made an account already, then you can use [this link](https://m.do.co/c/6be9c5acd3ca) and get $100 that expires after 2 months.

Once you have created an account or signed in using an existing one, go to https://cloud.digitalocean.com/droplets/new and create a droplet.
* Choose the highest Ubuntu LTS version (20.04 as of writing this)
* Select the standard $5 plan - This will be enough to run the bot with, you can even run multiple on the same server.
* Choose a region in which the VPS will be located.
* Choose authentication method, a one-time password is easy but vulnerable (you can always set up an SSH key later)
* No volume or backups is needed
* Click on "Create" to create the VPS

If you chose the one-time password authentication, you will then receive an email with the IP, username, and password.

# Connecting to your VPS

You need an SSH client to connect to the VPS. Go to https://www.putty.org/ and download the installation file. Once it is downloaded, run the file and go through the installation process.

When PuTTY has been installed, run it and do the following:

* In the hostname box, paste in the IP of your VPS, then name the VPS in the box below - this will save your session so you can easily connect to your VPS later on
* If it is your first time connecting to the server, it will ask you to enter the password from the email you got. Copy the password and right-click on the terminal to paste it in, then hit enter (you will not see the password because it is hidden)
* If the password was correct, you will then be asked to enter a new password. This password will be used to connect to the VPS from now on. Enter a password and hit enter.

You're now connected and sign in to the VPS.

# Downloading NodeJS

Connect to the VPS and sign in.

Paste in the following commands:

```
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt-get install -y nodejs
```

This will install NodeJS v14.x together with NPM.

Once done, you can check if NodeJS and NPM are installed by checking their versions.

```
node -v
```

and

```
npm -v
```

# Downloading the bot

The same process as on your desktop, see [installation guide](https://github.com/idinium96/tf2autobot/wiki/a.-Installation#downloading-the-bot)

```
git clone https://github.com/idinium96/tf2autobot.git
```

Once the repository has been cloned, navigate to it

```
cd tf2autobot
```

Install dependencies

```
npm install
```

# PM2

To run the bot 24/7, you need to run the process in the background. If you run the bot with `node app.js` or `npm start`, the bot will stop when you close the terminal.

Use PM2 to run the bot in the background, see the [guide](https://github.com/idinium96/tf2autobot/wiki/e.-Running-with-PM2).