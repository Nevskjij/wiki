# Join Discord server to get notified
Make sure you've joined the [TF2Autobot Discord server](https://discord.gg/ZrVT7mc) and head over to [`#🆚roles`](https://discordapp.com/channels/664971400678998016/719391430669500447/721533052890644511) channel and react to the first message to get notified whenever an update has been released!

<div align="center"><img src="https://user-images.githubusercontent.com/47635037/88795539-c8c65580-d1d2-11ea-993e-4161083b3e36.PNG" alt="update-noti" style="display:block;margin-left:auto;margin-right:auto;width:400px;height:250px;"></div>

# Updating the bot

Updating the bot is the same for both Windows and Linux.

Open up a command prompt or terminal/ssh window and navigate to your `tf2autobot` folder

`cd path/to/tf2autobot` OR just `cd tf2autobot` if you follow the instructions in [Downloading the bot](https://github.com/idinium96/tf2autobot/wiki/Downloading-the-bot-on-Linux).

If your bot is installed on the Desktop you will use

`cd Desktop/tf2autobot`.

After that, you will download and install the newest version by typing

`git checkout master && git pull && npm install && npm run build`

Now all you have to do is restart your bot and you will be running the newest version.

# Possible errors
You have unstaged changes, meaning that you have modified a file in the repository. To get rid of these changes, use `git reset HEAD --hard`. 
Please note that this will delete all changes, if you have code you wish to keep, create a fork/copy of the repository on GitHub, and commit your changes to it.