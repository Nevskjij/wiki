This page will go through how to update the bot. If you have not downloaded the bot, then go to https://github.com/idinium96/tf2autobot/wiki/a.-Installation.

# Updating the bot

Open a command prompt or terminal and navigate to the tf2autobot folder

`cd Desktop/tf2autobot` if the bot is installed on the desktop.

Pull changes from remote repository

`git checkout master && git pull`

Install dependencies

`npm install`

Compile source

`npm run build`

The bot is now updated, restart the bot for the changes to take effect.

## Possible errors

### Unstaged changes

You have unstashed changes, meaning that you have modified a file in the repository. To get rid of these changes, use `git reset HEAD --hard`. Please note that this will delete all changes, if you have code you wish to keep, create a fork / copy of the repository on GitHub and commit your changes to it.

**(Create guide for forking repository)**